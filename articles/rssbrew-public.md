# RSSbrew 公开订阅源

最近修了几个小 bug，把 images 上传到了 [docker-hub](https://hub.docker.com/r/yinanc/rssbrew/tags)，也做了个 [demo 站点](https://demo.rssbrew.com)，账号密码 admin, changeme （当然公开使用的，也不要真的去 change）。为了让大家更方便体验 RSSbrew 的功能，我从自己的订阅里面挑选了几个 AI 处理过的订阅源，供大家订阅试用：

- [Paul Graham](https://public.rssbrew.com/feeds/Paul%20Graham/)
- [36 Kr AI 相关](https://public.rssbrew.com/feeds/36kr-AI/)
- [Hacker News 最佳评论周报](https://public.rssbrew.com/feeds/HN%20comments/)

在任意阅读器里直接订阅，大概长这样

![](https://img.1991997.xyz/i/2024/11/28/r3yiwj-0.png)

![](https://img.1991997.xyz/i/2024/11/28/re054q-0.png)

分别用到了 RSSbrew 的内容过滤，订阅源合并，AI 总结文章，生成周报的功能。欢迎大家到[项目主页](https://github.com/yinan-c/rssbrew)点个⭐，也欢迎大家提交 bug/feature request。关于如何配置请参阅我的[另外一篇文章](https://yinan.me/rssbrew-config)

RSSbrew 可以通过自定义 prompt 做到一些简单的翻译，如果需要更专业的 RSS 翻译功能，推荐大家使用 versun 的[RSS Translator](https://rsstranslator.com)，也是用 Django 做的。当然也可以两个一起用！

## Disclaimer

所有公开订阅源均由 RSSbrew 处理后生成，原始内容来源于以下站点的 RSS 订阅源。
- [36氪](https://36kr.com)
- [Paul Graham](https://paulgraham.com/)
- [Hacker News RSS](https://hnrss.org)

公开订阅源仅用于 RSSbrew 功能演示，内容版权归各站点/原作者所有。如有侵权，请联系删除。
