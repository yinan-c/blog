# 弃用 memos

之前在博客中顶栏有一个 memos 的链接，现在还能[访问](https://memos.yinan.me)，解析到我部署的 memos instance。但我最终还是停用了。

原因如下：

1. 经过 v0.22.0，memos API 有个较大的变动，很多开发者（甚至我自己也在写一个 Alfred workflow 都不能再用了），我觉得软硬件即使是大升级，也不应该有 "Break" Changes，当然你也可以选择不升级。
2. 官方没有提供数据库导出到纯文本的方案基本，我之前基本是靠在 DEVONthink 中订阅 RSS 来实现导出的，而之前 private note 无法通过 RSS 订阅，为此我还在本地也部署了一个内网访问的 memos instance。
3. 功能增减太过频繁，最新版本似乎连 RSS 也没有了。

以上类似的想法，写过一条更为啰唆点的 [memos](https://memos.yinan.me/m/dRyEhke4qYwMBB8az2Nvqu)。

虽然作为开源项目，memos 不可谓是不成功的，况且用户也不能像要求商业项目那样去让开源项目维护者。但因为这是一个笔记应用，而笔记最重要的是通用性和稳定性（也就是能在任何一台电脑，任何一个应用内都能看到）。

关于这个，Obisidian 的 CEO 写过 [File Over App](https://stephango.com/file-over-app)。

考虑到这些我还是乖乖用回[纯文本 + Git](https://meganesulli.com/blog/sync-obsidian-vault-iphone-ipad/) 的方案，用 Obsidian 编辑。最近也在试用一个叫作 [blinko](https://github.com/blinko-space/blinko) 的应用，和 memos 很像，但是主打 AI 搜索+对话。

离开笔记应用不是没有成本的，转移就是一个，memos 仅有数据库保存方式，转移起来还挺麻烦 (again, file over app!)。我现在用以下方式，
1. Obsidian 有一个 memos sync 的插件，可以直接导入每日笔记。
2. Blinko 可以从 memos 数据库文件导入。
3. 直接读取数据库文件，想办法导出纯文本。
