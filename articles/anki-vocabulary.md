# 划词制作 Anki 卡片

最近在研究背单词（奈何来英国几年了，才发现单词才是短板，惭愧），一方面我在尝试不同的背单词软件，另一方面也在折腾划词生成 Anki 卡片，来建立自己的生词库。

关于背单词软件，建议大家看少数派的这篇文章以及底下的评论，[5 个维度、6 个 App，帮你选出最适合自己的「背单词神器」](https://sspai.com/post/87587)。或者可以网上找一些 Anki 卡片组，推荐两个制作精良的卡片组。

- [4000 Essential English Words (all books) [en-en] - AnkiWeb](https://ankiweb.net/shared/info/1104981491)
- [English Synonyms and Antonyms Workbooks - AnkiWeb](https://ankiweb.net/shared/info/1498738333)

本文主要介绍如何用划词工具制作 Anki 卡片，模板教程主要是根据[老黄老巢](https://www.laohuang.net/20171214/anki-definition-word-template/)的教程基础上进行了一些修改。

## 达到的效果

最终在浏览器用 ODH 划词翻译之后选择恰当的意思，可以将当前句子（附带可点击的 URL）以及对应的英，中文意思（默认先显示英语释义，点击后显示中文释义）添加到 Anki 中，并且制成 Defination-Word 和 Word-Defination 两种卡片。

![word-def](../output/pics/word-defination.gif)
![def-word](../output/pics/defination-word.gif)

## 需要的软件
- Anki and AnkiConnect 插件
- [Online Dictionary Helper](https://chromewebstore.google.com/detail/online-dictionary-helper/lppjdajkacanlmpbbcdkccjkdbpllajb?hl=en-GB)
- [模板下载](../output/pics/Antimoon.apkg)，在[原4.0模板](https://arc.net/l/quote/oqpbgclk) 的基础上略有修改

## 配置 ODH

在此，我仅仅分享一下合适我的配置：

- 我不需要全部的意思，只需要符合当前语境的意思，所以选择了 Consice 而不是 Glossary or Collins
- 我需要中文在我点击的时候显示出来，所以我选择了 Collins EN-CN 字典
- URL： 在我想看原文上下文的时候点击 Sentence 部分即可跳转
- add-dw: 这一项不为0代表同时添加 Definition-Word 卡片

![odh](../output/pics/odh.png)

具体每个配置的详细意思可以参考这篇博客，[Antimoon 划词助手兼容模板 3.0 - 老黄老巢](https://arc.net/l/quote/oqpbgclk) 或者项目的 [GitHub 主页](https://github.com/ninja33/ODH)。

## 修改卡片显示项目(可选)
上面提到我在老黄老巢的模板上进行了一些修改（比如把 glossary 改成 consice 只显示一种释义，比如增加 URL 和默认隐藏中文释义），主要是为了适应我的需求，你也可以根据你的使用习惯在 Card-type 中进行修改卡片模板。

![](../output/pics/card-type.png)

## Further Reading

- [https://github.com/ninja33/ODH](https://github.com/ninja33/ODH)
- [背单词软件Anki之Antimoon特色模板教程(definition-word卡片自动生成)_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1zW411a7Dz/?p=1)
- [Antimoon 划词助手兼容模板 3.0 - 老黄老巢](https://arc.net/l/quote/oqpbgclk)
- [请找一个解释要配的上我这个单词 — 老黄老巢](https://www.laohuang.net/20171214/anki-definition-word-template/)
- [Antimoon - How to Learn English effectively](https://www.antimoon.com/how/srs.htm)
- [5 个维度、6 个 App，帮你选出最适合自己的「背单词神器」](https://sspai.com/post/87587)