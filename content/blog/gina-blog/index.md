---
title: "How to harass your elected officials using TypeScript"
date: 2020-07-17
draft: true
---

Folks

Friends

Fellas and fellettes

As you all know, it's apocalypse season. Now more than ever, in times like these, in uncertain times, and in hard times - We all need to come together and harass our elected officials.

The US response to COVID-19 has been an abject failure, at each and every level of government. This is not controversial or interesting or technical, so I'm not going to write further about it.

Instead, lets shift focus to Gina Raimondo, and how I've made it my quarantine mission to bother her. You see, Gina is the leader of the small state of Rhode Island. Rhode Island fits into my internet narrative because, for at least one point in time, it had [record low COVID numbers](https://www.nbc-2.com/story/42302778/connecticut-rhode-island-only-two-states-reporting-decline-in-new-covid19-cases), relative to the rest of the country. It had succeeded in flattening the curve.

Enter Gina Raimondo. Gina saw these numbers, and thought they looked great. I agree Gina! Great numbers! On July 4th however, Gina decided to get bold, and started initiating [**"Phase 3"**](https://www.ri.gov/press/view/38720) or whatever the hell. This phase can basically be translated into *"hooray, corona times are over! party time!!!!!* 🥳"

This is an obviously bad idea, especially with the rest of the country still floundering around in the COVID swamp like fools. I've been pretty frustrated by Gina's actions and statements, so I tried channeling that into something *"productive"*(?) with my [dumb web app](https://corona-gina.app/). It's an expression of my anger and pure bewilderment of this government, and I had fun making it. Let's talk about how I did it.


### TypeScript is good and you should use it
When harassing your local government: type-safety is of utmost importance.

I shouldn't need to espouse the virtues of TypeScript to you by now. You've undoubtedly [seen](https://slack.engineering/typescript-at-slack-a81307fa288d) [a trillion](https://www.reddit.com/r/typescript/comments/aofcik/38_of_bugs_at_airbnb_could_have_been_prevented_by/) [articles](https://medium.com/@jtomaszewski/why-typescript-is-the-best-way-to-write-front-end-in-2019-feb855f9b164) with the exact same premise. I'll just ask... If you're not using TypeScript in 2020: What's wrong with you?

Some say that TypeScript is only good for large "projects that scale", including Microsoft themselves. I say that this is baloney. TypeScript is good for *any* size project. Want to print "hello world" and be done with it? Use TypeScript. I'm serious.

To give a short explanation of what this even is: TypeScript is a *"typed superset"* of JavaScript. That's an overly complex way of saying that **all JavaScript programs *are also* TypeScript programs**. TypeScript is not a magical new language. It is just some really nice features and keywords slathered over JavaScript that, in my opinion, essentially "fix" the language and make me want to use it.

The biggest and boldest benefit of using TypeScript is the full [intellisense](https://en.wikipedia.org/wiki/Intelligent_code_completion#IntelliSense) you get inside of the [VS Code](https://code.visualstudio.com/) editor. Intellisense is like autocomplete on your phone, except that it works. It brings the coding experience much closer to C#, in that methods actually *tell you* what the hell they want, and the editor will screech if there's a problem. This is unlike JavaScript, which often feels like coding in feedback-less empty and silent bottomless hole of despair and doom. 

*"The only people who don't like TypeScript are the people who haven't tried it yet!"* - me, 2020

#### A case study in bad corporate decision-making
Not everyone shares my beliefs. Pretend, for the sake of argument, that you are a high-level executive at a leading fintech company. A team of smart people in this company do some research for their next project, and decide to use TypeScript as their language of choice. Neat! I am very in favor of this, and so are the higher-ups who approved this team's choice. They start developing the app in TypeScript, enjoying the freedom and simplicity.

Enter the TypeScript-hating executive. This executive is not afraid to make his case against TypeScript to each and every engineer of the company. He does just this in a large conference call. His reasoning for why the team **must** switch back to plain JavaScript **immediately** are:
1. If you can't learn JavaScript you're bad and shouldn't be hired
2. Something something extra build-pipeline steps

Even though they did half the project in TypeScript, they were forced to strip away all their types. This story is, to me, a great tragedy, much sadder than whatever garbage Shakespeare ever put out. It genuinely upsets me that - because **one** high-up dude had a biased and incorrect understanding of a technology - a team had to stop what they were doing and make their software actively worse halfway through development.

My point with this big long anecdote is: Fight for the technology that you think is best. In this case, the people in this story *did* fight to use TypeScript, and still lost. Management sided with the executive here, and that's a shame. Thankfully for me however, my bad web app is a purely personal project, so I can just go nuts with it and do whatever.


### Going nuts with it and doing whatever - Why I'm using **Preact** instead of **React**
Unlike React, Preact will not work on granny's web browser. More on that later.

Preact is also not maintained by Facebook, *The Evil Corp™*. Instead, Preact is maintained instead by, uh... [some dude]? And has some [mysterious corporate backers]. So this is better, I think? 

Anyway, not the point. I'm using Preact instead of React because of the all-important **P**. This stands for **petite**, meaning Preact is a *petite* React. Essentially it enables the same great developer experience of React, with the added benefit of getting to ship a much less bloated runtime to users.

Preact accomplishes this by doing away with a lot of the React cruft, namely the [reimplementation of every standard browser event into "synthetic events"]. Facebook had a good reason to do this for React: They wanted to support legacy Internet Explorer, for all the Facebook grannies and gramps out there.

This is fine and well and "noble" I guess, but I think it's becoming rapidly unneeded to degrade your app by supporting legacy browsers. For the most part, everyone's switched to their phones, which usually come preinstalled with *evergreen* browsers like Chrome or Safari. Second, even if there are some stragglers out there on their old Gateway's running IE 6, we really need to draw the backwards-compatibility line *somewhere*, ideally before we go [totally bonkers, like some people]. My deepest condolences go out to all the Gateway fans.


### yarn good, npm bad
I'm using the yarn command-line tool, instead of the more popular npm. I'd really like to ask you all, [why are you still using npm in 2020?](https://iamturns.com/yarn-vs-npm-2018/) Yarn has a much more pleasant-looking CLI (command-line interface, pronounced like CLEE!), and to me, still feels faster than npm. Have you ever really *looked* at the output that npm spews all over the sacred console? It's a disgrace. The colors were chosen seemingly at random, whenever it does *anything at all* it **flashes** and **SCREECHES**, and it draws all sorts of ASCII rectangles whenever something needs an update.

My complaints here seems arbitrary and stupid, and sure, I'll concede both of those points. However, to me, these things matter. I'm a *"visual person"*, for whatever that's worth, so if I'm going to pick a CLI to stare at all day for hours-on-end, it better not look like ass. Like npm. Yarn has subtle, soft colors, smoothly-animated progress spinners, and the lock files look a lot cleaner to my eyes. Of course, you should never look directly at the lock files with your unworthy human eyes, but sometimes I like to check up on what **the machine** is doing.

Yes, it's maintained by Facebook, a [very] *[not] [good]* company. But guess what? [npm] is owned by Microsoft now, and they are also an organization that will burn in the [corporate] [version] [of hell]. It's 2020, and all your fav CLI tools are cancelled. Congrats!

![sonic](sonic.jpg)


### Pair program whenever you can
In the grand-scheme of things, you don't matter. I don't matter either. Do [pair programming](https://en.wikipedia.org/wiki/Pair_programming). Or, do the much more extreme, but still great in it's own way, [mob programming](https://mobprogramming.org/). I have enough pop-off energy on this subject to write an entire blog series on it, but I won't do that now. Instead, I'll keep this section relevant.

I had an idea for something to implement - I wanted the COVID cases to *count up* over time, rather than jump to the number on page load like it was doing before. My buddy was available to pair at the time, so we started working on the feature. I was a bit fried from it being 7pm after a long workday, and so was my co-programmer. However, we each melded our minds together to complete the feature. While we were both exhausted: I used my knowledge of the hooks API to get the timer itself working, and he used *deductive reasoning* to figure out that the animation should be **exponential**, rather than animate via pre-cached speeds like we had at first. The code we wrote that day is [right here](https://github.com/akc8012/gina-rona-app/blob/master/src/components/CaseCounter.tsx), and it really turned out great. I don't think it would have been possible using the traditional "everybody split up!" methodology of software development.

A younger, less-mature me would have been bummed that I couldn't figure out the exponential animation by myself. Now, **2020 Apocalypse Year Andrew** knows better. I don't matter, and neither do you. The software matters. To make the best possible software, one must throw away their ego. Destroy your ego. Throw it in a box, and throw that box off a cliff. Into a fire. Acid fire. Where we're going, you won't be needing that.

### Conclusion

