+++
title = "Should I Vibe Code?"
date = "2026-08-06T02:28:34+02:00"
+++

As we all know, AI tools are constantly getting better.

Every ~4 months, there's a new SOTA model, and the last-generation models (~4 months old) are basically no longer worth using.

So, should we just stop coding and rely only on AI agents to do all of the architecture, design, and implementation?

**NO.**

I use AI daily for my job and for other unrelated, complex work.
AI agents are very good if you know what you are doing, and they will massively increase your productivity.
They will save you a lot of time during those six-hour debugging sessions where there's one small edge case, but you just can't find it.
Or when you need to do some annoying array indexing, get it exactly right, and are losing your mind trying to keep track of all those indices (I personally suck at algorithms).
Basically, AI agents don't care how boring a task is.
They can work nonstop for 10 hours on the most boring debugging sessions.

Another good use case is AI reviews, but they are not perfect.
Agents like to bring up completely unnecessary problems sometimes.
Problems that will occur once in the lifetime of the universe
But it's better to handle them and add more code, right?

Or my favorite: when agents write migrations for code that hasn't even been committed.

My next point is that GPT models, as of this writing (GPT-5.6 Sol), think of you as a god.
I somehow steered mine to push back heavily when I say something dumb, but that doesn't stop it from making something up with extreme confidence and telling me it's a big problem.

BTW, Claude models are not much better.
They like to stop listening, go off on their own, and do their own thing, so they're just the opposite end of the spectrum.

<br />

But what if you, the reader, don't have any experience coding?

IMO, it's still not too late and never will be.
New engineers are going to be born in the future, and they will need a deep understanding of these systems because AI agents are still not good enough.
Honestly, I don't think they ever will be.

AI needs an extreme amount of information about a topic to be good at it.
For example, there's so much web slop that AI can create a pretty nice website, right?
Have you seen AI websites?
It's the same design again and again.
Even from different models, you can just smell the slop.

What if, for example, you don't like the generic AI slop website design and want something of your own?
In that case, you could try steering it one element at a time toward what you want, starting from the slop template it made.
But I've actually tried it, and it was so bad.
The website still looks bad to this day.
The only websites AI has designed well for me are minimal ones, and they're like 100 lines of HTML.
For example, [status.adamekka.com](https://status.adamekka.com) ([source](https://github.com/Adamekka/status/blob/main/src.js)) is 30 lines of JavaScript and looks good because there's basically nothing on the website, so nothing can go wrong.

And this is web dev, where most of the AI slop is.
Don't get me started on API design.
By default, it writes such bad API interfaces for libraries and even common interfaces within an app.
I have to steer it so much with my preferences and explain exactly what it needs to do when writing each class just so the result isn't unusable slop.
It still looks a lot worse than if I had manually designed it.
So my workflow often involves doing an AI slop cleanup after each feature to keep the codebase clean.

The problem with AI API design is that it's trained on so much random stuff that it can reproduce common patterns, but it's bad at understanding tradeoffs when designing a library.
So I would be surprised if AI API design and app architecture ever got good.
It's going to get decent at best, but not good.
You still need well-designed APIs for big libraries, and I don't think a good, 100% vibe-coded library is ever going to exist.

So I think you should still learn to code, even if you haven't started yet.
