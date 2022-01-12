---
date: 2020-06-07T13:33:57-05:00
title: 'What is agile (for a software developer)?'
tags: ['agile']
---

(Adapted from an internal talk)

The tech world has seen a lot of talking about agile/scrum, almost to the point that it is the silver bullet for software engineering. The new meaning is even in the definitions that google gives.

<!--truncate-->

{{<figure src="./Agile-google.png">}}

On the contrary, [some people absolutely hate it](https://hackernoon.com/what-happened-to-software-development-j92032w9), [some say that process matters far less than everyone pretends it does](https://blog.pragmaticengineer.com/surprising-things-about-working-at-tech-unicorns/#:~:text=5.%20Process%20matters%20far%20less%20than%20everyone%20pretends%20it%20does) (which I agree). I also saw a very interesting theory from HackerNews: the agile process improves the productivity of a C-level developer, but it slows down your A-level developer at the same time, so everyone ends up at B-level. Since C-level developers are much more common than A-level ones, the overall gain is positive.

So... **What does it mean to be agile?**

After serving as the scrum master for my team for a few months, and going through trainings and tests (thanks to my employer - [Oracle Data Cloud](https://www.oracle.com/applications/customer-experience/data-cloud/), now I'm a [Certified SAFe® 4 Advanced Scrum Master, SASM](https://www.youracclaim.com/badges/cbe4665a-c54d-469f-baea-116d1eeb90ca/linked_in_profile)), below is my take on this question.

{{<figure src="./SASM.png">}}

## Agile Basics

### Values

- **Individuals and Interactions** over processes and tools
- **Working Software** over comprehensive documentation
- **Customer Collaboration** over contract negotiation
- **Responding to Change** over following a plan

### Principles

The Manifesto for Agile Software Development is based on twelve principles:

1. Customer satisfaction by early and continuous delivery of valuable software.
2. Welcome changing requirements, even in late development.
3. Deliver working software frequently (weeks rather than months).
4. Close, daily cooperation between business people and developers.
5. Projects are built around motivated individuals, who should be trusted.
6. Face-to-face conversation is the best form of communication (co-location).
7. Working software is the primary measure of progress.
8. Sustainable development, able to maintain a constant pace.
9. Continuous attention to technical excellence and good design.
10. Simplicity—the art of maximizing the amount of work not done—is essential.
11. Best architectures, requirements, and designs emerge from self-organizing teams.
12. Regularly, the team reflects on how to become more effective, and adjusts accordingly.

## What's next

There are many companies to help businesses to implement Agile/Scrum (huge market if we keep the hype), the big ones are [Scrum Alliance](https://www.scrumalliance.org/) and [Scaled Agile (SAFe)](https://www.scaledagile.com/). Below is what I learned from my SAFe trainings.

### What is SAFe

Here is a graph trying to describe SAFe ([their website](https://www.scaledagileframework.com/#) has an slightly updated version). They try to fit everything into a single graph and end up with this overwhelming thing.

{{<figure src="./SAFe.png">}}

I'm not a fan that many words are used to refer to similar things, and I found out things are much simpler if I look at this graph through a fractal/recursion lense.

### Building block

The agile team is at the bottom left corner, consisting of the product owner, the dev team, and scrum master. The product owner defines the work; the dev team do the work; the scrum master facilitates the whole process.

The first key is the **feedback loop** - plan, execute, review, retro.

1. In the sprint planning (one or two weeks), the team breaks down the work into small pieces, prioritizes them, puts the most important work in the sprint and commits to finish them.
2. During the sprint, priority might change, but since the each task is small, the team can pivot fairly easily.
3. All the work will be reviewed / tested before it is claimed done.
4. At the end of sprint, the team will retro on what went well, and what could be improved in the future.

With the positive (hopefully) feedback loop, the team gets better at the estimating the work, finishing the tasks collaboratively, and eventually the productivity is more stable and **predictable**.

### Scale on the first dimension - time

The above loop happens on other time frames as well. On the daily basis, the standup is to plan the day and retro the previous day. Every quarter there is a planning as well. The rituals are more formal, take more time in the larger loops, and the impact is bigger.

### Scale on the second dimension - "space"

From top to bottom, the graph is divided into several layers, all of them operate similarly, except that the higher layers are larger organizations. For example, on the second layer, the "agile team" consists of product manager, system architect, and RTE. At the point you can probably infer that the RTE is the "advanced" scrum master. This team operates on a larger, more abstract level, coordinates the agile teams underneath it. Obviously, the total number of layers depends on the size of the company.

## Conclusions

There you have it, agile in a nutshell. It is not a silver bullet, but it made my life easier.

## Appendix

SAFe collects a lot of materials about teamwork / productivity, and tries to fit them into their framework. Below are some materials that I found useful and interesting.

### The five dysfunctions of a team

{{<figure src="./5-dysfunctions.png">}}

### Three elements of intrinsic motivation (of knowledge workers)

{{<figure src="./3-elements.png">}}

### Kanban

[Here](http://brodzinski.com/2013/07/cumulative-flow-diagram.html) is a great introduction on cumulative flow diagram.

Arrival curve (todo) and departure curve (done) should more or less be in parallel.

Limit WIP to minimize context switch and reveal bottleneck.

### Where does work come from

- the top: planned work
- the side: bug reported from clients => unplanned work
- the bottom: from the dev team
