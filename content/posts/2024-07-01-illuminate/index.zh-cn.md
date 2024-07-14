---
title: '用谷歌AI来总结我自己的论文——Illuminate试用小记'
date: 2024-07-01T22:12:02-04:00
tags: ['Google', 'AI', 'Illuminate']
images: ['./abstract.png']
---

（很久没有接触这种学术材料了，本文尝试重温一下论文格式。）

## 摘要

谷歌最新的实验性 AI 产品能从学术论文生成讨论音频。作者使用自己的论文作为输入，试用了该产品，发现生成的音频对论文的总结还是比较精确的。虽然目前该产品还有一些局限，但是未来可期。

## 背景简介

谷歌内网开大会，有个 AI 项目 demo，[Illuminate - turn academic papers into AI-generated audio discussions](https://illuminate.withgoogle.com/home)。给它一篇（或者几篇）论文的 URL，它会生成一段 3-5 分钟左右的音频，形式类似于学生和老师的对话，内容是对这个研究的主要内容、意义的讨论。我的第一感受是，这个东西感觉很厉害，但是实际上用处不大吧？演示者说主要用处是 1. 有的人更喜欢用听的而不是用看文字来学习；2. 这个方法能够帮助到不识字的人群。我心想不识字的人应该不会对论文感兴趣吧？可能现在先从论文开始做，因为论文的格式套路还是比较固定的，比较适合作为机器学习的材料，等以后再推广到其他文字材料？不过我心想，管他呢，要不把我之前的一些论文都放上去玩一下？它网站上提供的几个例子都是计算机、机器学习相关领域的，不知道对于化学类的文章表现怎么样？

## 实验步骤

想到了马上就做，首先把论文放到自己网站上，再把 URL 填进去，稍微等待几分钟就会生成一个音频文件。用 [blackhole](https://existential.audio/blackhole/) 折腾一下 QuickTime 录屏，就得到了音频文件（由于手速比较慢，音频开始有些空白 😂）。音频文本底稿由 https://go-transcribe.com/ 生成。

## 结果与讨论

我们使用一篇 2014 年（十年了！）发表的[论文](./David-CF3.pdf)为例。原文我不建议大家读了（除非您对以钯催化的乙烯聚合有特殊兴趣），[摘要](https://pubs.acs.org/doi/10.1021/om500699t)也是一大段话，各种数字、字母、符号，黑话一大堆，很唬人。摘要图倒是相对比较清楚，但是里面的信息还是比较繁杂，门槛还是太高。

{{<image src="./abstract.png" caption="摘要">}}

工具输出的[音频](./David-CF3.m4a)不到两分半钟，讨论了这篇论文的研究对象（一类用于乙烯聚合和共聚合的钯催化剂）、为什么研究很重要（生成的聚乙烯在生活中应用广泛）、相关的一些基本概念（乙烯聚合、动力学过程）、关键的发现（两个动力学过程的活化能不同）、主要研究方法（核磁共振光谱）。作为论文作者，我认为这个对话作为（可能是装作）对这个研究稍微感兴趣的人的简要入门介绍是合格的。当然音频也略有不足，例如个别专业单词估计是因为比较生僻，发音很奇怪（chelate），还有一个人说完话另一个人接话太快，不像是自然的对话。

## 结论

这个 AI 工具完成度还是比较高的，实验观察得到的生成音频对输入论文的研究主题、主要发现的总结都是比较到位的，未来如果加入更多功能（例如能够让用户提问）用处能更大。

## 补充材料

音频文本：

Student:
Let's unpack a paper titled differentiation between chelate ring inversion and aryl rotation in a cf3 substituted phosphine sulfonate Palladium methyl complex. What's the core idea here?

Teacher:
Right on. This paper is a deep dive into the world of palladium complexes, specifically those with ortho phosphine sulfonate ligands. These complexes are catalysts for olefin polymerization and copolymerization.

Student:
Olefin polymerization you say, that sounds pretty important.

Teacher:
Absolutely. It's a key process in making plastics and other materials we use every day. These palladium complexes are catalysts, meaning they help speed up and control the reactions that make these polymers.

Student:
So what's the big deal about this particular paper?

Teacher:
Well, the authors focused on the dynamic properties of these complexes, like how they change shape in solution. They used NMR spectroscopy techniques to track these changes.

Student:
NMR spectroscopy huh, that sounds pretty technical.

Teacher:
It is, but it's a powerful tool for studying molecules. In this case, they were particularly interested in two processes chelate ring inversion and aryl rotation. These are like two different ways the molecule can change shape and understanding them is crucial for designing better catalysts.

Student:
I see. And what do they find out about these processes?

Teacher:
They found that the barriers to these processes are different, meaning one is easier for the molecule to do than the other. This is important because it gives us clues about how these catalysts work and how we can tweak them for better performance.

Student:
So it's all about understanding how these molecules change shape, right?

Teacher:
Exactly, and this paper provides some valuable insights into that.

Student:
That's exciting. It sounds like this paper could have a real impact on the field.

Teacher:
I think so too, it's a solid piece of work that adds to our understanding of these important catalysts.

Student:
Definitely. It's always cool to see new tools being used to tackle these problems.

Teacher:
I agree.

Student:
And this closes our discussion of differentiation between chelate ring inversion and aryl rotation in a cf3 substituted phosphine sulfonate Palladium methyl complex. Thank you.
