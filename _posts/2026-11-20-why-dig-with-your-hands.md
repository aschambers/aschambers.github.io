---
layout: post
title: "I was against AI. Here's what changed, and what didn't"
date: 2026-11-20
categories: [ai]
---

## Why I was against AI use

Preface: When I say AI, I mostly mean chatbots and coding agents that I use to research things, fill in gaps Google leaves, and build small prototypes. I'm not talking about vibe coding whole apps or generating whole posts, which a lot of people assume is what "using AI" means.

I used to be completely against AI, and honestly I still am. The way it's used and marketed has always felt like corporate greed. I see AI sold as a way to do more with fewer people, and I feel like the executives pushing that care more about cutting costs than making anything good. Not to mention all the slop and the awful ways people use the technology. None of that has gone away. What changed is that I stopped seeing the tool and the way it's sold as the same thing.

About a year ago, I started using AI to help me with some bracket code I was working on for Zygarden, a tournament platform for competitive Pokémon. I had built lookup tables, along with functions that used them to generate the lines connecting each matchup to the ones that they feed into, adjusting dynamically to the number of participants. That worked for up to 32 participants, but I wanted to expand it to 128, for both single and double elimination.

The process of building that for up to 32 participants was already very time consuming, and a friend had been using AI and spoke highly of some things it could help with, and so I thought I'd try asking AI to help with this endeavor. AI got a lot wrong as there were many places where bracket matchups were not aligned with bracket lines. Doing this using AI was still way faster to go in and hand tune things than to create all of that by hand.

The studies on how much time AI really saves are [mixed](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/). AI seems to help most on well-defined, self-contained tasks, like [this one](https://arxiv.org/abs/2410.12944), and least when experts are working in code they already know well. Expanding my bracket code was the first kind. Even with all the hand tuning, I felt like the use of AI saved me a lot of time.

To check the work, I needed to see the brackets at every size from 2 to 128 participants, for both single and double elimination. Doing that by creating tournaments by hand means more than 250 of them, so I set up a way to load test brackets instead. A few settings in the app let me choose which bracket to load, and whether the bracket comes from local files or a hosted copy. That let me check every participant count and spot ones where the matchups and connecting lines didn't line up:

![Test settings for generating 128-participant brackets](/assets/images/test-bracket-service-diff.png)

![Code change adding a source option for test brackets](/assets/images/test-bracket-settings.png)

AI has also sped up how I learn new things. When I was figuring out how to set up an app initializer in Angular, AI gave me an answer, and when I asked where that came from, it took me straight to the part of the Angular documentation that explained the setup. Before, I'd google how to set one up, find a Stack Overflow post or a blog post showing how other people handled the same problem, and then verify the result myself. Now I still end up verifying the source, just a lot faster.

AI also helps when I hit something like writer's block, where I know what I want to build but I'm having trouble getting my thoughts in order, and can provide a very good starting point for what I want to build. A good example would be deciding how to organize shared components, tokens, and styles in a large Angular app, where I'm not sure where to even begin. I can ask AI about various approaches and think about the pro's and con's of each.

There's an analogy I like for this. Why dig with your hands when you can use a shovel? I think it's mostly right, but the shovel isn't the whole story. The rest of this post is about where the use of AI stops working.

## The environmental impact and regulations

One could argue that the environmental cost of huge data centers is reason enough not to use AI at all. I get that, and I hate the impact too. These facilities use a lot of electricity and water, and the people who live near them feel the impact first. Data center electricity use is way up from a few years ago, and [that's expected to keep rising](https://www.iea.org/reports/key-questions-on-energy-and-ai/executive-summary).

Things don't have to be this way though. [Apple says](https://www.apple.com/uk/environment/pdf/GBEN_Apple_Environmental_Progress_Report_2025.pdf) they have powered every facility with renewable energy since 2018, including their data centers, and their latest report says all of the [2.5 billion kWh](https://www.datacenterdynamics.com/en/news/apple-data-centers-consumed-more-than-25-billion-kwh-over-2024) their data centers used in 2024 came from renewable sources. Not every company builds data centers that carefully, and I think the ones that don't are a big reason people hate both data centers and the people in tech pushing AI.

Cleaner power doesn't fix everything though. The costs are still real, and they hit hardest in the communities next to data centers, where water and the power grid get strained. I'm not trying to brush that off. But when I look at the big picture, AI is only one piece of a small share of the problem today. [All data centers together, not just AI, account for around 0.5% of global CO2 emissions](https://carbonbrief.org/ai-five-charts-that-put-data-centre-energy-use-and-emissions-into-context), while [livestock is estimated at 12-20% of global greenhouse gas emissions](https://www.climatechangenews.com/?p=52515) and [fashion at up to 8%](https://news.un.org/en/story/2025/03/1161636). That doesn't make AI's footprint okay. I'd just rather hold everything I use to the same standard than single out one thing.

So for me, the question isn't really whether to use AI or not. Holding everything to the same standard means asking what each thing costs, in energy and in what I stop learning, and what I get back. Using AI to speed up work like my bracket code, where I can check the results and fix what's wrong, is worth that cost to me. Flooding the internet with low-effort content isn't.

I think AI use should be disclosed, and that we should stay critical of how people use AI. Most of my objections come down to not knowing whether a person made something, whose work the model was trained on, or what the environmental cost was. [California](https://www.morganlewis.com/pubs/2026/08/new-california-ai-disclosure-rules-become-operative) and [the EU](https://www.dynamisllp.com/knowledge/ai-disclosure-in-2026-recent-developments-and-practical-steps-for-brands-and-influencers) have started down this road, and both now have rules for labeling AI-generated content.

I'd also want to know what AI costs the communities that host its data centers. [California](https://www.insideenergyandenvironment.com/2026/09/californias-new-data-center-package-highlights-growing-state-focus-on-energy-water-and-environmental-impacts/) and [New Jersey](https://news.bgov.com/artificial-intelligence/new-jersey-joins-states-cracking-down-on-data-center-energy-use) now require data centers to report their energy and water use, which seems like a good starting point.

## The archaeologist

Not every job needs a shovel. An archaeologist doesn't dig with one, because the careful part is the point. A brush and a trowel are slower for a reason, and breaking something to save time isn't saving anything.

This is the line I draw for myself:

- Using AI to debug a problem I understand, a shovel.
- Using AI to explore an unfamiliar area, then checking what it told me and learning the material myself, a shovel.
- Using AI to produce something I don't understand and using the result anyway, a crutch.

Code I don't understand is code I can't maintain, fix or explain, so I use AI where I could check the answer myself. If I can't tell a good hole from a bad one, I shouldn't be the one digging.

Logs are another place AI helps. At work, we have a JSON column in SQL Server logging tables, and searching that when you don't know what you're looking for can take a very long time. Comparing behavior across a microservice setup is just as slow, like checking QA against UAT. This is where AI really comes in handy. I can export the logs to a file and have AI read through hundreds of entries, tell me what's missing between the two environments, and point out what went wrong and when. The output can miss things, so I treat every finding as a lead and check each one myself. That speeds up troubleshooting, but I still have to think about what the findings mean and decide what to do next.

Video games have a version of this that makes sense to me. In speedrunning, tool-assisted runs have to be disclosed. Using tools to learn tricks and practice is fine, and pretty much every speedrunner does that. Using them during the actual run without saying so defeats the point. People forgive a run that was disclosed, but not one that was hidden. I think AI works the same way. The tool isn't the problem, hiding the fact AI was used is.

## Art

I know there are a lot of creative professionals that now use AI to brainstorm and get past a blank page, and that's close to how I use AI when I'm having trouble with my thought process. An artist can ask for a dozen concepts, a few color palettes, or a different angle on a scene they can't quite picture.

That helps them find a starting point, and then the drawing is theirs, with every line, choice, and mistake coming from them. I don't have a problem with that. My line is the finished piece, because the making is the part I care about.

With code, the hole is usually a means to something else, so a shovel makes sense. With art, the making is often the whole point. When someone draws, paints, or composes, what I value is the time, the choices, and the person behind the work, and a generated image skips all of that.

I also can't separate this from the corporate greed I mentioned at the start. Many artists say their work was used to train these tools without their permission, and I think that deserves to be taken seriously.

I know plenty of people see this differently, but I'd personally like to know if an image or piece of art was AI-generated.

## Takeaways

So, why dig with your hands when you can use a shovel? I will, as long as I know what I'm digging for and I'm honest that I used a shovel. Here's what I try to follow.

- Use AI for the slow, mechanical parts, so I have more attention left for the work that needs judgment.
- Don't use AI to skip understanding. If I couldn't check an answer myself, I shouldn't trust the answer.
- Treat what AI gives me as a lead. Read the code, test it, and do my own research before I build on the results.
- Say when I've used AI. Hiding that I did is the real problem, not the tool.
- Where the process is the point, like art, do the work myself. AI can help with ideas, but not the finished piece.