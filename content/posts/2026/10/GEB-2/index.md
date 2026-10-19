---
title: "GEB Reading Notes #2 — Chapters 1 and 2"
date: 2026-10-17T14:31:06-04:00
tags: ["GEB", "Reading Notes"]
images: []
---

(Translated from the Chinese version with the help of ChatGPT.)

## Three-Part Invention

Following the [music recommendation](https://ocw.mit.edu/courses/es-258-goedel-escher-bach-spring-2007/pages/readings/), I listened to the first piece of *The Musical Offering*, BWV 1079: the three-part ricercar.

{{<youtube BtnZmHj3d70>}}

The dialogue *Three-Part Invention* features three characters: Achilles, the Tortoise, and Zeno. Here are a few of the jokes and references:

- The Tortoise mentions zero, but Achilles steps outside the system and points out that zero has not been invented yet. This is also a nod to Carroll's *Two-Part Invention*.
- Achilles and the Tortoise, both figures in Zeno's paradoxes, start talking about Zeno and his paradoxes. This is a play on tangled levels and self-reference.
- Achilles mentions "the Sixth Patriarch Zeno" and the famous debate about whether it is the wind or the banner that moves, or whether it is the mind that moves. Apparently, Achilles has misattributed to Zeno a story about the Zen master Huineng, the Sixth Patriarch of Chan Buddhism. When the Tortoise points this out, Achilles says he can never keep Zeno and Hui-neng straight. The Chinese translation adapts the joke rather than translating it literally. In English, Achilles is trying to recite the names of the six patriarchs of Zen, but gets them wrong and declares that the sixth patriarch is Zeno. The joke hinges on the similar spellings of *Zen* and *Zeno*.
- Zeno himself appears, and Achilles and the Tortoise begin debating whether it is the wind or the banner that moves. More tangled levels and self-reference.
- The Tortoise does not know Zeno's name, yet Zeno calls Achilles by name.
- Zeno mentions "my master, the Fifth Patriarch." Is Zeno actually Huineng after all?
- Zeno goes on to tell a story about Achilles and the Tortoise, saying that they were persuaded by a passerby to race. In Hofstadter's version, that passerby is Zeno himself! More self-reference.

## Chapter 1

The author poses a puzzle: given a formal system with the initial string WJ as an axiom and a set of inference rules, can we derive WU? In other words, is WU a theorem of the system?

Trying a brute-force approach, I can find what look like patterns. But the more I try, the less progress I seem to make, until I start getting frustrated. The author suggests that all of this illustrates something special about human intelligence.

- **The human ability to step outside a system.** Does the thing I am working on actually mean anything?
  - When we get tired of reading, we stop and take a break.
  - Watching television:
    - Tuning in to a particular channel (within the channel system).
    - Changing channels (within the television system).
    - Turning off the TV (stepping outside the television system).
  - In human affairs, different systems are intertwined. It may not always be possible to draw a clear distinction between inside and outside a system, or between different levels of a hierarchy.
- **Three modes of human thinking:**
  - *m-mode* (mechanical mode; the Chinese translation uses J to represent the mechanical mode).
  - *i-mode* (intelligent mode; the Chinese translation uses W to represent the intelligent mode).
  - *u-mode* (un-mode, or Zen mode; this will be explained in more detail later. The Chinese translation calls it the "Wu mode," using the Chinese character 无, meaning "nothing" or "non-being," while keeping the same letter U).

There doesn't seem to be an intuitive way to determine, in a finite number of steps, whether WU is a theorem. (Spoiler: the answer will be revealed in Chapter 9, the final chapter of Part I.)

One thing to note: the letters in the English and Chinese editions do not correspond exactly. In the English edition, the puzzle asks whether MU can be derived from MI, rather than whether JU can be derived from JI. This difference may become more significant as the book progresses.

## Two-Part Invention

For this section, I listened to BWV 772.

{{<youtube eVkNc3LSgOo>}}

Hofstadter places Lewis Carroll's *What the Tortoise Said to Achilles* here. In the music, two voices engage in a dialogue; in the text, two characters do the same.

- After their race, Achilles catches up with the Tortoise and sits on his shell. They exchange a few words, and the Tortoise says, "You flatter me—or rather, you flatten me." The Chinese translation's rendering of the pun feels a little awkward, so I checked the English original. Sure enough, this is a difficult one to translate, and the translator did their best. The original reads, "You flatter me — FLATTEN, I mean." The joke is a pun on *flatter* (to praise someone excessively) and *flatten* (to press something flat).
- The two characters talk about shorthand not having been invented yet, and about admiring Euclid even though he will not appear for several centuries. Hofstadter echoes this absurdity in *Three-Part Invention*.
- At the end, the Tortoise says that his cousin, the Mock-Turtle, wants to rename Achilles "Taught-us," while Achilles proposes renaming the Tortoise "A Kill-ease." It seems that the two are exchanging names, or at least playing a game of mutual renaming. Here are the English names and their wordplay:
  - **Tortoise**: the tortoise.
  - **Achilles**: the Greek hero Achilles.
  - **Mock-Turtle**: a character from *Alice's Adventures in Wonderland*. The name comes from *mock turtle soup*, a British dish made with substitute ingredients to imitate the expensive soup traditionally made from turtle. Lewis Carroll turned the dish into a character.
  - **Taught-us**: sounds like *Tortoise* and means "taught us."
  - **A Kill-ease**: a playful resegmentation of *Achilles*, suggesting something like "a person for whom killing comes easily."

## Chapter 2

The author introduces a *pq-system* and then shows that we can map *q* to "equals" and *p* to "plus," thereby giving the system a meaning through an isomorphism.

But what I found most illuminating is that the meaning need not be unique. For example, we could instead interpret *q* as "minus" and *p* as "equals." Mathematically, these interpretations are equivalent; neither is inherently better than the other. Yet the first interpretation feels much more intuitive and natural to me.

The author then discusses Euclid's proof that there are infinitely many prime numbers. It is concise, elegant, and convincing. Every step in the reasoning seems obvious, yet the conclusion as a whole is not obvious at all.