# AI 总结 RSS Feeds

## 项目地址

[yinan-c/RSS-GPT](https://github.com/yinan-c/RSS-GPT)

## 信息爆炸的焦虑

RSS 是我一直在用并且非常喜欢的信息获取方式，你可以把你喜欢的内容创造者或者大多网页上更新的内容聚合在一个地方集中阅读。但不加筛选，富含噪音的 RSS 在订阅中堆积也很让人疲惫不堪。每天几百几千条未读产生，如果强迫症和焦虑症患者强求 RSS inbox-zero 的话，久而久之会浪费很多的时间执着于清空未读上面，实属折磨。

![Heavy Inbox](pics/Inbox.png)

并且即使你全部清空了阅读，多半情况下 inbox 空空，脑袋也空空，因为这时候你已经没有精力去消化，而是像短视频一样消费 RSS 内容，你只是得到了匆匆而过的信息，没有内化沉淀成知识，而代价却是时间，注意力和精力。

## RSS 过滤

在这种情况下，摆脱 [FOMO - Fear of missing out](https://en.wikipedia.org/wiki/Fear_of_missing_out) 的心态是很重要的。另外一个非常有效的方法就是，对 RSS 进行关键词过滤，只保留自己真正感兴趣愿意花时间阅读的内容。

我目前知道有两个小工具可以做到 RSS 过滤，https://siftrss.com, 另外还有一个 feedless.org。我只用过前一个体验很不错，可以根据 description 可以看到很多人都在用，作者也一直为爱发电。

## RSS 翻译

前段时间在看到了一个这样的项目 [RSS-Translation](https://github.com/tjsky/RSS-Translation/tree/main), 作者写了非常详细的教程教你如何用 GitHub Actions，来自托管翻译 RSS 订阅源。原项目应该是[这个](https://github.com/talengu/rss-translate)。

## RSS 摘要

![RSS-GPT](pics/RSS-GPT.png)

其实对我来说，相比较翻译，对 RSS 全文的中文总结更有价值，因为我可以快速了解到这篇文章的主要内容，来决定是否进一步精读。所以我最近写了这样一个工具，可以全文总结 RSS 订阅源，提取关键词，生成摘要附在原文之前，方便阅读。除了 AI 摘要，另外还有合并 RSS 订阅源，过滤订阅源的一些功能，可以详见 [RSS-GPT](https://github.com/yinan-c/RSS-GPT)。如果想要自己配置自己喜欢的订阅源，可以 fork 我的项目，部署十分简单，只需要更改 config.ini，给 Repo GitHub Pages 权限，以及设置 WORK-TOKEN（Github Token to access GitHub pages）, U-NAME (Git commit user name), U-EMAIL (Git commmit user email), OPENAI_API_KEY 这四个 repo_secrets 即可。我之后可能会写一篇更详细的中英文指南。

这里也汇集几条我公开的 [RSS 源](https://yinan.me/RSS-GPT/rss/)，欢迎大家订阅。
