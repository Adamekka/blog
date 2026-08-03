+++
title = "The Perfect Library"
date = "2026-08-03T15:40:00+02:00"
+++

In my life, I've written a lot of libraries.
A lot of them are unfinished; some are finished.
Over that time, I've kind of learned what makes a good library.

Have you ever asked yourself: do I even need to write documentation or a getting-started guide for my library?
My library must be perfect.
I WROTE IT.
I UNDERSTAND IT.
Well, that doesn't mean some random guy on the internet using your library will understand it.

But what if the library could be so good that everything about it, including its entry point and all its options and features, would document itself?
Actually, you still have to know what the entry-point type is because you have to call something.
But what if all the options of the _entry-point type_ are exposed? Then you don't have to search for anything; it's all there.

Let's call the _entry-point type_ `HTTPClient`.
It'll come from our shared library as a struct containing enum properties, and you just pick exactly what your app needs from each one.

```swift
struct HTTPClient {
    let authentication: Authentication
    let retryPolicy: RetryPolicy
    let cachePolicy: CachePolicy
    let decoding: DecodingStrategy
}

enum Authentication {
    case none
    case bearer(token: String)
    case basic(username: String, password: String)
}

enum RetryPolicy {
    case never
    case immediate(maxAttempts: Int)
    case exponentialBackoff(maxAttempts: Int)
}

enum CachePolicy {
    case disabled
    case memory(maxSize: Int)
    case disk(directory: URL)
}

enum DecodingStrategy {
    case json
    case propertyList
    case custom(Decoder)
}
```

Usage:

```swift
let client = HTTPClient(
    authentication: .bearer(token: apiToken),
    retryPolicy: .exponentialBackoff(maxAttempts: 3),
    cachePolicy: .memory(maxSize: 50_000_000),
    decoding: .json
)
```

This is what I think makes a **perfect** library: there are no properties to provide after construction.
The caller knows exactly what the library can do because they're forced to pick one option from each.

This pattern can be used even further.
For example, in my SwiftUI app development, I've created an `AppWrapper` that owns features I frequently use across many apps.
This type wraps the app's entry point and controls stuff like ATT, UMP, Google Ads initialization, onboarding, the splash screen, accounts (including premium handling), and a lot more.

At the time of writing, this is exactly what the type handles:

```swift
public struct AppWrapper<Account: Accountable, Content: View>: View {
    @State private var account: Account = .init()
    @State private var localizationManager: LocalizationManager = .init()

    @AppStorage(.firstLaunch) private var firstLaunch: Bool = true
    @State private var splashScreen: Bool = true
    @State private var trialPage: Bool = false
    @State private var didNotifyAccountReady: Bool = false
    @State private var advertisingState: AdvertisingState = .notStarted

    private let showATT: Bool
    private let advertisingConsentProvider: AdvertisingConsentProvider
    private let splashScreenConfig: SplashScreenConfig
    private let onboardingViews: @MainActor () -> [OnboardingViewType]
    private let trialPageConfig: @MainActor () -> TrialPageConfig
    private let onboardingStart: (() -> Void)?
    private let onboardingEnd: (() -> Void)?
    private let onAccountReady: ((Account) -> Void)?
    private let content: (_ canRequestAds: Bool) -> Content
}
```

And this is how it's used:

```swift
AppWrapper<Account, ContentView>(
    showATT: false,
    advertisingConsentProvider: .disabled,
    splashScreenConfig: .init(iconShadowConfig: nil),
    onboardingViews: { onboardingViews },
    trialPageConfig: { trialPageConfig },
    onboardingStart: nil,
    onboardingEnd: nil,
    onAccountReady: { account in
        self.delegate.onAppsFlyerSessionReady = { [weak account] in
            Task {
                await account?.retryPendingPurchaseValidations()
            }
        }
        if AppsFlyerLib.shared().isSessionReady() {
            self.delegate.onAppsFlyerSessionReady?()
        }
    },
    content: { _ in
        ContentView()
    },
)
```

Note that this makes it extremely simple to create a new app because all I have to do is construct a single type.
It's also fine to make breaking changes because the compiler will tell me when an argument is missing from the initializer.

BTW, this isn't the only type using this pattern.
There are at least 30 types in my shared lib that use this pattern and save me a lot of time.

And I hate the builder pattern.
Just pass the whole array during construction instead of calling `addProperty()` 67 times and then forgetting to add another property because the compiler didn't enforce it.

A good API exposes every option, requires important decisions during construction, and lets the compiler catch incomplete configuration.
