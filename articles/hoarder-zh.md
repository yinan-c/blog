# Hoarder - 自托管 AI 书签管理软件

对于书签管理，我目前的工作流是这样的：自建 [wallabag](https://wallabag.org/) 保存稍后读，[Anybox](https://anybox.app/) 管理书签并通过 Alfred 快速调用，然后用 [DEVONthink](https://www.devontechnologies.com/apps/devonthink) 本地归档 wallabag 的稍候读和 Anybox 的书签，方便全文搜索。为了实现自动化，我还写了[一个脚本](https://github.com/yinan-c/Anybox-sync-Devonthink/blob/main/anybox_to_devonthink.py)，可以自动把 Anybox 的新链接同步到 DEVONthink（这个脚本是在 [Anybox alfredworkflow](https://alfred.app/workflows/anybox/anybox/) 基础上改进的）。

这套流程一直运行得挺顺畅，但我还是有两点不太满意：

> 1. Anybox 缺少全文搜索功能。截至2024年11月，这个呼声很高的功能还停留在[Under Review](https://anybox.canny.io/feature-requests/p/full-text-search)阶段。

> 2. 书签整理不够智能。虽然 Anybox 的收件箱理念不错，从收件箱再整理到文件夹、标签，还能依赖 Smart Folder 功能帮忙分类管理，但每周要把他们手动打标签或者移入文件夹还是太麻烦了。在保存了海量书签后，我还是更习惯用搜索（可惜又没有全文搜索）。所以目前我还是倾向于在 Anybox 和 Wallabag 不整理，只有收件和存档两个状态，存档之后依赖 DEVONthink 的全文搜索 + Smart Rules 再自动分类整理。

最近发现了一个新项目 [Hoarder](https://github.com/hoarder-app/hoarder)，主打 AI 自动打标签，准备体验一下，看看能不能取代或者补充 Anybox。（作为一个爱好 self hosted 和囤积资料的人，Hoarder 这个名字就很对我胃口 🤭）

第一印象相当不错，感觉是个成熟的产品：有 iOS 应用支持分享菜单，有 Chrome 扩展方便保存，还能存笔记和图片。AI 自动标签功能，可自定义 prompt，能帮我省去手动整理的麻烦。

不过要完全替代 Anybox，还需要补齐以下几个功能：

- [REST API](https://github.com/hoarder-app/hoarder/issues/43) - 用于数据自动化导入/导出和开发 Alfred 插件
  > 目前只提供命令行工具， REST API 会在[0.18.0 下一个版本支持](https://docs.hoarder.app/api/)
- [便捷的数据导出和备份](https://github.com/hoarder-app/hoarder/issues/75)
  > 截图、本地缓存、链接等数据的导出功能还不完善。
- 离线归档
  > 现在只支持纯文本缓存和截图。据说后续会支持更多格式（截止2024年5月，已在规划中）。
  更新：到2024年11月，已经支持用 [monolith](https://github.com/Y2Z/monolith) 实现完整网页存档，解决了链接失效的问题。
- [本地网页抓取](https://github.com/hoarder-app/hoarder/issues/172)
  > Anybox 和 [SingleFile 扩展](https://github.com/gildas-lormeau/SingleFile) 的配合就很完美，可以把登录后的或者付费墙后的内容直接通过 API 保存下来。
  >（另外，这样还解决了 SingleFile 元数据只保存域名前缀的问题 - 直接用 SingleFile 下载到 DEVONthink 时只能看到类似 https://github.com 这样不完整的地址）

还有一些锦上添花的功能建议：
- RSS 订阅功能
  > [linkding](https://github.com/sissbruecker/linkding) 和 [wallabag](https://wallabag.org/) 都有这个功能。我现在就使用 RSS 把 wallabag 的内容同步到 DEVONthink，和用 [kindleear](https://github.com/cdhigh/kindleear) 订阅 wallabag RSS 每天晚上推送稍候读到 Kindle。

Hoarder 虽然暂时还不能完全替代我现有的工具链，但作为一个活跃开发的开源项目，发展势头很好，值得持续关注。