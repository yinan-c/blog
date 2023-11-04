# 折腾

最近又开始折腾博客了，我用的是 [Pyboke](https://github.com/yinan-c/pyboke)，一个通过 Python 实现的简约的博客生成器。

简约，换句话说就是能够实现的功能比较简单。所以会有很多想法, 有些接入第三方 API 修改模板即可实现，有些则可能需要修改 Pyboke 源代码。虽然这些想法也不一定都会实现，但还是记录下来，之后有时间再慢慢折腾。

## ChatGPT 总结

首先就是 AI 总结，ChatGPT 已经帮我总结了不少 [RSS 订阅源](https://yinan.me/RSS-GPT/index.html)。在决定深入阅读前，可以先借助 AI 总结的内容判断是否感兴趣，效果很不错。

尝到甜头后我就想能不能也用在自己的博客文章中，方便游客快速了解文章内容。首先的想法是加一个 metadata 条目 'summary'，然后在提交文章时自动调用 ChatGPT 总结，把结果填入 summary 中，因为之前主页上的预览也是这样做的，再加上我之前也写过 [RSS-GPT](https://github.com/yinan-c/RSS-GPT)，所以花了一些功夫就写出大概功能了。但是目前还有几个问题没解决：

1. 是否所有文章都需要总结？是否要在 metadata 文件中加一个条件判断？比如有些文章，about，contact 等，可以加一个 `ignored = True` 标签。
2. 文章的 metadata 是在运行 `pyboke` 之后才生成的，如果要加条件判断，那么就需要在生成 metadata之后，再运行脚本进行 ChatGPT 总结。
3. 那么，是否应该引入 YAML 格式的 front matter，来代替现在 toml 格式分开存储的 metadata？这样就可以在文章中直接设定是否需要总结，而不需要在生成 metadata 之后再手动修改。

在这些问题还没有定论之间，我还没有想要把自动总结加入 Pyboke 的源代码。目前以我可怜的博文数量以及更新频率来看，手动让 GPT-4 总结，然后添加到 metadata 后通过 Jinja 模板自动渲染，应该就够了。 

我还在考虑是否需要将 AI summary 附加在 RSS 上，那么在这种情况下，需要在发布文章之前就附上总结，并且修改 `atom.xml` 的模板使其包含总结信息。这样自动化总结或许是更好的方案。

如果你想要折腾自动化的方案，并且用的是 Hugo，可以参考大大的小蜗牛的[这篇文章](https://eallion.com/ai-summary/)。

## 评论和点赞

之前看过水八口的一篇帖子[第三方评论之2023年版](https://shuiba.co/third-party-comments-2023)详细对比了不同方案的优缺点。

最终决定用了[giscus](https://giscus.app/)，利用的是 [GitHub Repository](https://github.com/yinan-c/pages-comment) 的 discussions 功能，所以既可以在 Repo 里评论，也可在博客内评论。好在设置非常简单，在 template html 加上一段 js 脚本即可。除了评论点赞必须要登录 GitHub 账号外，目前没有什么太大问题。

这两天又在逛博客，发现了一些很有趣的方案，[Yuxi&Yuqi](https://yuxiyuqi.com)的评论是用的[twikoo](https://twikoo.js.org/en/)，[koobai](https://koobai.com/) 用了 [Artalk](https://artalk.js.org/en/)，[子舒的博客](https://zishu.me/)用了 [emaction](https://github.com/emaction/emaction.frontend) 来实现 emoji reaction，点赞无需登录，也可以自己部署[后端](https://github.com/emaction/emaction.backend)。后续可能会考接入我的博客。

## 全文 RSS

这是之前一段时间 (2023-09) 就已经实现的功能。原项目的 RSS 带了 Markdown 的格式符以及截取到前 150 个字符。我给 Markdown 转成了 HTML，并取消了字数限制，这样就可以直接在 RSS 阅读器里看到全文了。

## Memos as in-line "Tweet"

我想要把生活中简短的点滴放在博客，而不是仅仅写长 posts，推特本来是一个理想的平台，但是因为 Twitter API 以及 RSS 的封闭，除了 [embed Twiiter](https://publish.twitter.com/)，我好像没有特别好的办法把上面的内容搬运过来。[Koobai](https://koobai.com/memos)的“唠叨”使用的是 [Memos](https://github.com/usememos/memos) 方案，而[Yuxi&Yuqi](https://yuxiyuqi.com/timeline/) 则使用了时间线的方式, 目前我还没搞懂是用的啥方案还是自己搭的。

关于这个功能，我目前并不急着实现，就算之后要选择第三方实现，数据的 privacy, self-hosted 对我来说，应该是首要考虑因素。

## 展示个性化订阅源

使用 [rssTea](https://github.com/avadhesh18/rssTea) 展示播客订阅源，或个性化的订阅源，比如即刻，v2ex动态等。

## 暂时搁置的功能
搜索和标签, 目录

目前来看，Pyboke 以 metadata 以 toml 格式保存以及与文章分开存储的方案，相比较于 YAML front matter，各有利弊，前者保留了 Markdown 的文本格式，后者则可以直接在文章中修改 metadata。目前新添加的功能例如 首页预览，文章内总结，确实需要在渲染生成 metadata 文件之后，然后手动进入文件修改。但是目前以我更新博客的频率来看，还是可以接受的。如若以后有了更多需要手动添加的 metadata，例如标签，那么我或许会考虑引入 YAML front matter。最后一句话赶紧掐断我写下更多的折腾的想法吧，Hey, if it ain't broke, don't fix it.

## Further Reading

- [博客 AI 摘要及优化 - 大大的小蜗牛](https://eallion.com/ai-summary/)
- [第三方评论之2023年版 - 水八口](https://shuiba.co/third-party-comments-2023) 