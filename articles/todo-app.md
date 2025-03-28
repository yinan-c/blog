# 苹果端 Todo App 简单比较

继半年多前从 Things 转移到 OmniFocus 之后，今天又在探索苹果端几大 Todo App，主要比较了 Things, OmniFocus 以及 TickTick（唯一跨平台，已经赢了🤭）。

## Things

先说说老朋友 Things，Logbook 显示我从2022年的7月开始用到了2023年的11月15日，等了一年半的 Things 4，始终没有等到。

不过 Things 3 还是一如既往美观简洁好用，可惜相比较 OmniFocus 缺了以下我觉得很有用的功能：

- Filter/Smart List: Shortcuts 目前半残，如果我不能在组会前，看到在 PhD Area 完成了哪些项目我怎么给老板交差？
- Review Perspective: OmniFocus 可以帮你 keep track review 列表，Things 只能手动 Review。
- Automation: 在 OmniFocus 里可以写脚本把符合某些条件的 Todo 自动归类，或者 Tag。

## OmniFocus

我是从 OmniFocus 4 更新（2023年底）之后才开始重度使用的，上面其实已经把我这半年多用 OmniFocus 的感受列的差不多了，唯独有一点我还希望能够加上的，就是 Kanban View。

我的任务通常会卡在某个节点比如说，计算中，或者等待回复，而不是简简单单的 0-1 两个状态，而 kanban 以及 Things 的 Heading 就很好地处理了这个问题。OmniFocus 虽然有 Nested Task，但是使用下来更像是子/母任务的从属关系，描述任务的状态我更多用的是标签，但是仍不如 Kanban 拖拽来的直观。

>EDIT: 用 Tagging 作为 Kanban 的坏处在于它不是 exclusive 的，把任务从一个标签拖拽到另一个会让它同时打上两个标签，作为 Kanban 显然不理想。好在[论坛](https://discourse.omnigroup.com/t/sub-tag-exclusivity/41773/5)里有人提到用 Command + 拖拽就可以实现转移标签。

>另外，如果需要一个 Kanban board based on Tagging，可以看一下[这个插件](https://omni-automation.com/omnifocus/plug-in-kanban-board.html)，试用了一下还不错，从脚本上实现 exclusive tagging，把不同 board 的按钮放在工具栏也能实现在不同标签(Board)之间转移任务。比如说我现在的工具栏和 kanban 长这样：

![](../output/pics/kanban.png)

题外话，Things vs OmniFocus 的比较于我有点像 Anybox 和 DEVONthink 的比较，一个简洁漂亮，功能单一，能完成他该完成的，一个功能强大，有点 buggy，不够美观，上手难度偏高。

## TickTick

一度觉得很理想，有 Kanban，四象限，过滤器，还有经典的日历视图。
除了没有 Area 的概念，Project 多了可能会很乱。

但是为什么不让我在 iOS 端用国内滴答的账号？

>EDIT: 感谢读者提醒，把 App 语言修改成中文后，登录界面底下可以切换成国内滴答。我再体验几天，后续可能会更新详细体验和比较。

Update on 2025-02-24:

用了滴答几个月了，我的感觉是一个不错的有潜力的 todo app，虽然操作逻辑上不如 things 顺畅（比如说清单不能多选删除），但是胜在做好了功能和美观易用易上手的平衡点，且价格亲民。缺点是用户生态不如前两个软件，导致 [API](https://developer.dida365.com/docs#/openapi) 开发和其他软件的插件支持不多，且我最想要的按照创建时间排序根本没有，只能自己写了个脚本通过 API 手动获取。

还有一个很大的槽点就是官方备份导出是一份 csv，恢复备份的时候不能像 Things 和 OmniFocus 一样整个覆盖数据库，回到某一个时刻的状态，而是在你原有数据上增量恢复，除非你在恢复前手动清空你的账号（注意清单不能批量删除，只能一条一条右键-删除）。

![](https://img.1991997.xyz/i/0/2025/02/24/spmyc2-0.png)

## 其他玩家

我没有测试 Todoist，因为订阅费用实在太高，但是据说自然语言输入很好用。还有一些后来者：比如 GoodTask (in SetApp) 可以作为 Reminder 的强化版本。我没有考虑长期使用，所以这里不详细介绍了。

最后，Todo 只是帮助 prioritize 和 focus 的工具，为了 Get Things Done，一张纸也可以做到这样。所以没有最好的 Todo App, 只有最适合你的。

切忌陷入[效率陷阱](https://utgd.net/article/20657)。

切忌花在拖拽, Tag Todo 比实际完成 Todo 花的时间还要多。

切忌频繁更换工具，能用就不要动。
