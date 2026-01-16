+++
title = "Why AI Makes Everything Boring"
date = "2026-01-16T03:13:34+01:00"
+++

I remember in 2022 when OpenAI released GPT-3.5. It was a really interesting model at the time, and we didn't know what consequences of AI we'd be dealing with today.
I used it mostly for annoying school stuff like writing protocols.
But for programming it wasn't great, because all it could really do was write a simple function or a small algorithm.

Nowadays big companies say they'll replace devs every 3 months, but we already know where that leads.
AI is still not good enough for building big applications.

**But why does AI make everything boring?**

Well, before the "good" AI models, I wrote every little tool myself.
I read the README, the docs, learned about the tool or programming language, and did everything manually.
I really enjoyed writing small helper apps, because the side effect was that you learned a lot about the language and the tools you used.
For example, I learned Rust when I wrote [dotfile-manager](https://github.com/adamekka/dotfile-manager), which I still use to this day.
The code is very bad because I didn't even know what a struct was at the time, but I learned a lot about libgit2, paths on Linux, and more.

My earliest project where I learned what a function and an array are (and basically all the fundamentals) is [mpr](https://github.com/adamekka/mpr-install).
It's my first real programming project, it taught me what Git is, and it's in BASH - so BASH is the language where I learned the basics of programming.

**Now back to the present.**

Currently, if I wanna write some little helper tool, I don't really have the motivation for it, because you can just vibe-slop it so easily.
And then you don't even know how it works.
So you just say to yourself: "Why bother?" and vibe-slop it instead.

But then if you wanna do something larger, you lack the knowledge on the subject.
And learning while doing a big project is not optimal, especially for project structure.

**So what's the solution?**

Maybe don't use AI at all?
Maybe the real solution is to force yourself to learn, and use AI as a reviewer - not the developer.
Write a complex class, then ask it if it's optimal, and it'll say something like: you don't handle this scenario properly, your error handling is weak, etc.

One of the things I learned is that you should design the core project architecture yourself, and then let the LLM do the individual systems.
But even then, you just do the structure and have no idea about implementation details or edge cases.
And you learn **NOTHING**.

This problem might not have a perfect solution.

Stack Overflow is dead and everyone is using AI.

So the AI-as-a-reviewer option might be the best solution.
