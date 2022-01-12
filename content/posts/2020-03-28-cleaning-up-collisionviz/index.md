---
title: 'Cleaning up CollisionViz - advice to new programmers'
tags: ['clean-code', 'CollisionViz']
date: 2020-03-28T13:21:40-05:00
---

[CollisionViz](https://collisionviz.davidfeng.us/) is a data visualization app which shows car crashes in the New York City. I wrote it when I was at AppAcademy in 2017. Since then, I haven't spent a lot of time on it. Recently I found out that it stopped working. **Software is like cars - it needs maintainable.** In addition to fixing it, I gave it an [overhaul](https://github.com/davidfeng88/CollisionViz/compare/v1...v2). Below are some advice that I wise I knew when I first wrote CollisionViz, and hopefully it is applicable to other new programmers.

<!--truncate-->

## 1. Talk to the Users As Early As Possible

In v1, CollisionViz works like a video player - you click a "play" button and the car crashes appear on the map in the order of crash time. You can also pause the animation, adjust the play speed, etc.

{{<figure src="./v1.gif">}}

However, when I showed this app to my friends and interviewers, literally none of them used it that way. Most of them just click on the Google Chart to change the time (without me telling them to). Thus in v2 I changed the app so it's more intuitive. **No matter how cool you think your app is, run the idea with someone else to validate it ASAP.** Removal of the play mechanism makes it possible to clean up the UI and simplify data storage. Here is the v2 UI:

{{<figure src="./v2.png">}}

## 2. Remove Non-essential Parts

In v1, the map has four optional layers: heatmap, traffic, transit, and bicycling. Heatmap is relevant for the use case, but not the other three. Therefore, in v2, I removed them. Again, this makes it possible to clean up the code further.

In v1, I used Redux to handle global state, partially because I just want to show that I know how to use Redux. However, CollisionViz doesn't have deeply nested components that need to access top level state, where Redux is most useful. Therefore, again, I removed Redux.

These are just two examples of many things that I removed in v2. **It makes the essential parts easier to reason and maintain.**

## 3. Write Adaptors for External APIs

The reason v1 stopped working is that the crash data API changed its endpoint and several field names. I had to search and update several files to fix it. This is a sign of bad code organization. **I move all the code dealing with the crash data API into one single file - an adaptor, so that when that API changes (which is outside of my control), I only need to change this file.**

To generalize this idea, I made an adaptor for each of the third-party libraries that I use (e.g. Google Chart, Google Heatmap, etc.), alongside the code that uses the adaptor ([example](https://github.com/davidfeng88/CollisionViz/tree/v2/src/javascript/components/CollisionsFetcher)). Separating the adaptor also helps making my component smaller, which makes the code easier to understand.

The idea of adaptor was not new to me. I first learned it from _Code Complete_. However, back then I just thought it was a good idea, without internalizing it. Not anymore!

## 4. Organize the Directories Following Conventions

Following conventions would make your code look more professional and understandable ([Ref](https://stackoverflow.com/questions/22842691/what-is-the-meaning-of-the-dist-directory-in-open-source-projects)).

- `src/`: source files. Your code that feeds the compiler/build system.
- `dist/`, `public/`, `build/`: compiled/built code that is deployed. Hugo uses `public/`. GitHub Pages (where CollisionViz is hosted) do not support deploying from any of them yet, so I did not use them.
- `lib/`, `vendor/`: dependencies.
- `assets/`: static content like images, video, audio, fonts etc.

## 5. Do I Need to Update to the Latest Version of React/Webpack

**It's impossible and not necessary to be on the latest version of everything.** The tools/libraries are updated so frequently, and new ones are coming out every day. Sometimes it's not trivial to update, say from Webpack 3 to 4. Most of the time you don't need those latest features. As long as you fix security vulnerabilities (`npm audit fix`), you are probably fine. Spend your time on something else that's more valuable.

## Conclusions - Why Do You Keep Saying Clean Code

Because in workplace, unless your work is a greenfield project (relatively rare), programmers spend most time fixing bugs or adding new features to an existing project. Before you make any code changes, first you have to read the code and understand how it works. **Be kind to your co-workers and future self. Write clean code that's easy to understand.** This is so important, that if I could only give one piece of advice, it would be this. Unfortunately it was not stressed enough in schools and bootcamps.

(P.S. Somewhat surprisingly, interpersonal communication is also important in workplace for programmers. But maybe it's the topic for another post.)
