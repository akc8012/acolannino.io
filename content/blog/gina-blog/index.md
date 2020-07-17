---
title: "How to harass your elected officials using TypeScript"
date: 2020-07-17
draft: true
---

Folks

Friends

Fellas

As you all know, it's apocalypse season. Now more than ever, in times like these, in uncertain times, and in hard times - We all need to come together and harass our elected officials.

The US response to COVID-19 has been an abject failure, at each and every level of government. This is not controversial or interesting or technical, so I'm not going to write further about it.

Instead, lets shift focus to Gina Raimondo, and how I've made it my quarantine mission to bother her. You see, Gina is the leader of the small state of Rhode Island. Rhode Island fits into my internet narrative because, for at least one point in time, it had [record low COVID numbers](https://www.nbc-2.com/story/42302778/connecticut-rhode-island-only-two-states-reporting-decline-in-new-covid19-cases), relative to the rest of the country. It had succeeded in flattening the curve.

Enter Gina Raimondo. Gina saw these numbers, and thought they looked great. I agree Gina! Great numbers! On July 4th however, Gina decided to get bold, and started initiating [**"Phase 3"**](https://www.ri.gov/press/view/38720) or whatever the hell. This phase can basically be translated into *"hooray, corona times are over! party time!!!!!* 🥳"

This is an obviously bad idea, especially with the rest of the country still floundering around in the COVID swamp like fools. Gina's actions and statements have been pretty frustrating to me, so I tried channeling that into something *"productive"*(?) with my [dumb web app](https://corona-gina.app/). It's an expression of my anger and pure bewilderment of this government, and I had fun making it. Let's talk about how I did it.


### TypeScript is good and you should use it
When harassing your local government: type-safety is of utmost importance.

I shouldn't need to espouse the virtues of TypeScript to you by now. You've undoubtedly [seen] [a trillion] [articles] with the exact same premise. I'll just ask... If you're not using TypeScript in 2020: What's wrong with you?

Some say that TypeScript is only good for large "projects that scale", including Microsoft themselves. I say that this is baloney. TypeScript is good for *any* size project. Want to print "hello world" and be done with it? Use TypeScript. I'm serious.

To give a really short explanation of what this even is: TypeScript is a *"typed superset"* of JavaScript. That's an overly complicated way of saying that **all JavaScript programs *are also* TypeScript programs**. TypeScript is not a magical new language. It is some really nice features and keywords slathered over JavaScript, that, in my opinion, essentially "fix" the language and make me want to use it.

The biggest and boldest benefit of using TypeScript is the full [intellisense](https://en.wikipedia.org/wiki/Intelligent_code_completion#IntelliSense) you get inside of the [VS Code](https://code.visualstudio.com/) editor. Intellisense is like autocomplete on your phone, but it actually *works*, *really really well*, and brings the coding experience much closer to C#. This is unlike JavaScript, which often feels like coding in feedback-less empty and silent bottomless hole of despair and doom. 

*"The only people who don't like TypeScript are the people who haven't tried it yet!"* - me, 2020

#### A case study in bad corporate decisions
Not everyone shares my beliefs. Pretend, for the sake of argument, that you are a high-level executive at a leading fintech company. A team of smart people in this company do some research for their next project, and decide to use TypeScript as their language of choice. Neat! I am very in favor of this, and so are the higher-ups who approved this team's language of choice. They start developing the app in TypeScript, enjoying the freedom and simplicity.

Enter the TypeScript-hating executive. This executive is not afraid to make his case against TypeScript to each and every engineer of the company. He does just this in a large conference call. His reasoning for why the team **must** switch back to plain JavaScript **immediately** are:
1. If you can't learn JavaScript you're bad and shouldn't be hired
2. Something something extra build-pipeline steps

Even though they did half the project in TypeScript, they were forced to strip away all their types. This story is, to me, a great tragedy, much sadder than whatever garbage Shakespeare ever put out. It genuinely upsets me that - because **one** high-up dude had a biased and incorrect understanding of a technology - a team had to stop what they were doing and make their software actively worse halfway through development.

My point with this big long anecdote is: Fight for the technology that you think is best. In this case, the people in this story *did* fight to use TypeScript, and still lost. Management sided with the executive here, and that's a shame. Thankfully for me however, my bad web app is a purely personal project, so I can just go nuts with it and do whatever.

