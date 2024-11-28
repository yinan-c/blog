# 滴答清单体验

半年之前写过一篇[苹果端 Todo App 简单比较](https://yinan.me/todo-app.html)，主要是分析了 Things 和 OmniFocus 的优缺点，当时没有深度体验滴答清单（海外版称 TickTick），所以今天补上。

我是从 2022 年开始使用 Things3，2023年底换了 OmniFocus 4，一年后的今天我选择试一下滴答清单，所以这篇文章大多是关于 OmniFocus 和滴答清单的比较，会少量提到一下和 Things 的比较。

（P.S.: 现在 Things3 正在黑五7折优惠）

## 1 为什么要换

更换工具折腾是很大的时间精力和金钱成本，尤其是 TODO 和笔记，更何况我之前还写了把 Things/OmniFocus 的任务导出的脚本，换一个工具意味着重新来过。

但这一年 OmniFocus 确实也有让我体验不佳的点：
- 数据量大了会很卡，之前清理过一次了，我目前大概 2000 多个条目（包括已完成）不管是手机还是电脑端都不够流畅。
- 不够美观。见仁见智，我更喜欢 Things 的界面。
- OmniFocus 不像 Things 或者滴答清单那么，任务/项目完成了之后就完全从列表内隔离开，而是继续保持原有的结构在穿插在其他未完成的任务/项目中，导致界面很杂乱，虽然也可以通过改变视图为显示剩余，但这样又失去了结构，总之项目结构和整洁度二者只能去其一。
![](../output/pics/Omnifocus-random.png)
- 最主要的是产品的使用逻辑和我不对付，Things/滴答都有一个今日视图，给任务安排一个时间，他就会出现在那天的今日视图中，当然也可以通过 perspective 建立一个筛选过的今日视图（比如说筛选出`正在进行`标签或者有 defer/deadline date 是今日以及以前的任务。但我发现我就会滥用截止日期，过期的多了最后会导致对截止日期过期不敏感了，再加上杂乱的界面，会感觉失去重点和优先级，反而完成不了要紧事。

当然 OmniFocus 也有很多特别出彩的地方，比如说自定义 perspective（里面的条件很丰富），review 功能，插件自动化，Focus View（配合新窗口）等。具体可以见我之前的[文章](https://yinan.me/todo-app.html)。

## 2 滴答 vs OmniFocus

以下是我在会员免费期体验到的，有些功能可能免费版没有，另外限于时间，体验内容肯定不够完全。

### 优点：
- 外观：美观介于 OmniFocus 和 Things 之间。这两者的笔记一栏是长方形选中框的的下延展，随着笔记内容变多而变大，things 是纯文本格式， OmniFocus 是富文本，但是似乎只能通过粘贴保留格式，输入是纯文本格式，而且 OmniFocus 还挺卡的。滴答清单每一条任务展开之后占据右侧1/3窗口，完全可以当作一页纸来写（所以官方提供了转化为笔记的功能吧），还可以对内容进行加粗高亮，富文本。
- 操作和 Things 差不多顺滑，就是鼠标拖动支持的有点别扭（默认鼠标是选中文本，得选中左边的三条杠小图标才能拖动），目前来看键盘快捷键支持不如 Things 和 OmniFocus。
- 归档和完成的任务与开放项目隔离，眼不见为净。OmniFocus 所有都显示的话会很乱，见上图。但是我又需要看到能看到项目的结构，滴答正好通过最右边栏任务的详细页面做到了两个的平衡，也就是中间栏隔离，右侧栏保留结构（Things 的 Logbook 完全就没有原来的项目结构了，或者说 Things 本身除了 Heading 和任务内的检查事项就没有父子结构的概念，除非 Heading 整个被标记完成，才能在 Logbook 内还原 Heading 结构。
- 粘贴的链接可以自动识别并填充标题。
- 原生看板，OmniFocus 需要用插件配合标签，Things 只有一个只读的[第三方软件](https://apps.apple.com/gb/app/kanbanview/id1507458952)
- 完备的日历页面和任务+时间线的安排功能

![](../output/pics/ticktick.png)
![](../output/pics/things-heading.png)

### 缺点
- 虽然可以筛选，但是不能专注到某一个 project/area。
- 筛选可选项不如 OmniFocus 多，比如说没有办法实现根据创建时间/修改时间的筛选排序，这样很容易创建了就忘了，就连 Things 都能通过[捷径实现](https://www.icloud.com/shortcuts/967cbbc1c61546e4a869da6b35b59060)。
- 数据存储备份：OmniFocus 和 Things 似乎都是本地数据库+本地多副本备份+云端同步的方式，OmniFocus 支持手动打开 .ofocus-backup 回溯到某一个版本，然后支持本地覆盖云端/云端覆盖本地。滴答清单的数据好像都在云端存储，本地甚至不会显示出项目内所有已完成的任务（所以会在你搜不到东西的时候，有在云端中搜索的选项）
- 数据导出：滴答只支持任务导出到 csv，官方 API 只能导出未完成任务。OmniFocus 支持随意筛选项目后，导出 csv 和 .ofocus 文件。

### 其他有好有坏，见仁见智
- 使用逻辑：
  - OmniFocus 不同项目有区分，所以你可以很明显的看到项目的下一个任务（Next Available）是什么。
  - 滴答只有一个安排日期，OmniFocus 和 Things 都有两个日期，一个安排日期，一个截止日期。
  - 在 OmniFocus 中清单和任务没有太大的界限，可以互相拖动转换，Things 中任务可以被拖到 Area（也就是文件夹）下一层和项目平行，但是不能互相转换，Heading 可以转为项目，滴答清单自由度最低，任务，清单，文件夹，三种层级严格，任务 < 清单 < 文件夹，不能互相转换，除了任务可以有最多五层和其他任务的嵌套。但是拖动操作很不方便。
- 不会显示最近修改的任务列表，但是对于每一个任务有任务动态，还有垃圾箱，防止误删除。
- mac 软件的第三方支持：
  - Raycast: OmniFocus 没有，滴答很好用；Alfred: OmniFous > 滴答。
  - Popclip for [TickTick/滴答](https://www.popclip.app/extensions/x/htd93q), [Things](https://www.popclip.app/extensions/x/2xsjgt) and [OmniFocus](https://www.popclip.app/extensions/x/69vkqz) 都有。
  - Chrome 插件，TickTick 会更加强大一点, OmniFocus 只有一个第三方的添加。
  - 全局添加：OmniFocus 有 Services - Add to OmniFocus 和 Share menu 两项。滴答和 Things 都是快捷键唤出一个类似于 spotlight 的窗口添加，things 和 OmniFocus 会有对当前窗口的 context 自动填充。
  - API 与自动化: 
    - Things 有 [URL scheme](https://culturedcode.com/things/support/articles/2803573/), [Applescript](https://culturedcode.com/things/support/articles/2803572/), [第三方 python api](https://github.com/thingsapi/things.py)还有官方提供的[捷径库](https://culturedcode.com/things/support/articles/2955145/).
    - OmniFocus 有 Applescript 和 Javascript 来实现插件。而且可以通过直接读取 sqlite 数据库自动批量的导出数据，之前根据此写过一个[导出到 markdown 的脚本](https://github.com/yinan-c/Omnifocus-export-markdown)。
    - 滴答和 TickTick 有 [OpenAPI](https://developer.dida365.com/docs#/openapi) 非官方 [ticktick-py](https://github.com/lazeroffmichael/ticktick-py) (可能需要自行修改所有域名到 dida365.com) 等。

## 3 滴答的其他功能

除了基本的 tasks，滴答还提供番茄钟和习惯打卡，不过目前我没有找到合适的导出这两部分数据的方案，所以没有深度试。

## 4 迁移工作

Things 到滴答的迁移好像挺顺滑的（没有深度试），如果是反过来目前 Things 官方没有支持，只能自己从 API 或者导出的 csv 里面想办法。

OmniFocus 到滴答导入过程需要在 OmniFocus 选中任务再导出 csv，而且导入之后会丢失创建和放弃任务的时间点(后者应该是 OmniFocus 的锅，因为同样的问题在你归档旧的已放弃任务的时候也会出现，会重新变成未完成状态并且丢失放弃时间戳)。

我之前写过[OmniFocus](https://github.com/yinan-c/Omnifocus-export-markdown) 以及 [Things](https://github.com/yinan-c/things2md) 导出 markdown 的脚本，也可以用已完成项目按时间规律生成回顾/周报的功能，也可以把所有的任务分项目导出 markdown。配合 git 还可以追踪项目的变化情况。

迁移之后，花了点时间用各种 API 实现了导出所有未完成/部分完成任务，增量缓存 json，保存 markdown，再输出为 RSS。
其实折腾这么多就是为了能够把数据主动权在自己手里，如果平台/工具倒闭了（希望不要）至少自己还有数据能有退路再保留一份纯文本供自己阅读。

## 5 最后的话

关于 GTD（Get Things Done），完成事情是最终目的，折腾上花费的时间不如直接去完成你列表上的项目。这里引用一句话，

> The most important lever a leader has to create focus is to simplify the priority list. by [Rohan](https://alearningaday.blog/2024/11/21/creating-focus/).

关于工具，适合自己才是最好的。所以尽量秉承那句话 If it ain't broken, don't fix it.

## 6 相关

- [滴答清单/TickTick 官方API尝试](https://juejin.cn/post/7376484708547870731)
