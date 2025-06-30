---
title: '2022-08-07 周报01'
date: 2022-08-04T22:44:22-04:00
tags: ['周报', '隐私', 'AdTech', '英语', 'YouTube', 'Tadashi', '数学']
---

尝试写下周报，先随便写写，想到哪儿就写到哪儿，也不强求有什么主题之类，之后再慢慢改进吧。如果觉得有收获的话可能会坚持下去。

## 苹果要做广告业务？

苹果近几年的宣传重点之一是“保护用户隐私，屏蔽追踪”，俨然一副捍卫用户利益的模样。Meta 今年股价大跌跟这颇有关系（可自行搜索相关报道）。不过也不必太当真，资本主义嘛，怎么赚钱怎么来。苹果自家当然早就有广告业务（例如 App Store 的页面中有广告），但最近有报道（[1](https://digiday.com/media/apple-is-building-a-demand-side-platform/), [2](https://www.adexchanger.com/mobile/why-would-apples-idsp-succeed-when-iad-failed/)）说苹果要加大在广告业务上的投入，因为在招做 Demand Side Platform（DSP）的[高级产品经理](https://jobs.apple.com/en-us/details/200369598/senior-product-manager-demand-side-platform-ad-platforms)。哈哈，苹果[你这个浓眉大眼的家伙也叛变革命了](https://youtu.be/w_o8fOKZKX0?t=900)！

之前在 reddit 上也看到过标题党——[即使你没有苹果设备苹果也追踪你](https://www.reddit.com/r/privacy/comments/v624di/apple_tracks_you_even_if_you_dont_have_apple/) 。原文 PDF 太长，我也没读，真实与否请读者自己判断 😅。在这个时代，便捷和隐私的选择题，怕是只有理论上才能选择隐私了。

这周有一条爆炸性的新闻也引起了一些人对于 big tech 侵入隐私的担忧：Amazon 收购扫地机器人 Roomba 的制造商 iRobot。后续如何发展就只能拭目以待了。

## YouTube 上把视频进度条往前拖几秒时为什么还要等几秒才能恢复播放？

直观来说，几秒之前的视频信息应该已经下载到本地了，为什么还需要等待呢？为了减小数据传输量，视频都是经过压缩的。有的帧存储的是静态图，有的帧存的是从静态图推导生成的信息（比直接存静态图省空间）。所以当我们要跳到某一帧时，如果那一帧是静态图存储的，那就可以直接播放，否则要从那一帧之前的静态图帧计算生成，因此要花费时间（以时间换空间）。

完整回答在[这里](https://sidbala.com/h-264-is-magic/#:~:text=Let%27s%20say%20you%27ve%20been%20playing%20a%20video%20on%20YouTube.)。

## 学（一些没什么用的）英语

1. Floaty - 夏天游泳，飘在水上的不一定是救生圈 🛟 ，也可能是各种造型的玩具，甜甜圈 🍩，火烈鸟 🦩，鳄鱼 🐊，不一而足。这种漂浮玩具的俗名就叫 floaty。
2. [A ways to go](https://www.merriam-webster.com/dictionary/a%20ways%20to%20go) - 第一次看到 a 后面接复数的 ways，蒙了。结果意思是“还有很长的路要走”，非正式的说法。如果要我写的话我会用 [a long way to go](https://www.merriam-webster.com/dictionary/a%20long%20way%20to%20go)。
3. Swoosh - 耐克的对勾标志的名字。
4. [Dabble](https://youtu.be/ND2xk-naGWM?t=2231) - 原意是玩水，经常用来表达“随意玩玩，非专业地涉足某项活动”的意思。例句：- Do you still play the violin? - I try. I dabble.
5. [Shove something down someone's throat](https://youtu.be/ND2xk-naGWM?t=3744) - 直译是“将某物塞进某人喉咙”，经常用来表达“强迫某人接受某观点”的意思。

最后两项来自于 Jimmy O. Yang 在[谷歌的卖书宣传演讲](https://www.youtube.com/watch?v=ND2xk-naGWM)。如果你想我一样，第一次看视频记录下来一个单词，想要之后再回头来找在视频中出现的位置，并且视频在 YouTube 上有比较完整的内嵌字幕的话，可以点击`...` => 点击`显示转录` => 用浏览器来搜索单词（几乎把整个视频又看了一遍才想起来试试 🤦）。

## 勺子敲杯子，学习对称性

从[朝花夕拾](https://pywonderland.com/envelope-and-caustics/)上看到的，Tadashi Tokieda 教授在 Numberphile 频道上的一个视频，时间不长，11 分钟，很好玩。废话不多说，直接看吧。

{{< youtube MfzNJE4CK_s >}}
