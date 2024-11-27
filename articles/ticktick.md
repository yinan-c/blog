# 清单清单评测

半年之前写过一篇[苹果端 Todo App 简单比较](https://yinan.me/todo-app.html)，主要是分析了 Things 和 OmniFocus 的优缺点，当时没有深度体验滴答清单（海外版称 TickTick），所以今天补上。

我是从 2022 年开始使用 Things3，2023年底换了 OmniFocus 4，一年后的今天我选择试一下滴答清单，所以这篇文章大多是关于 OmniFocus 和滴答清单的比较，会少量提到一下和 Things 的比较。

（P.S.: 现在 Things3 正在黑五7折优惠）

## 为什么要换

更换工具折腾是很大的时间精力和金钱成本，尤其是 TODO 和笔记，更何况我之前还写了把 Things/OmniFocus 的任务导出的脚本，换一个工具意味着重新来过。

但这一年 OmniFocus 确实也有让我体验不佳不点
- 数据量大了会很卡，之前清理过一次了，我目前大概 2000 多个条目（包括已完成）不管是手机还是电脑端都不够流畅。
- 不够美观。见仁见智，我更喜欢 Things 的界面。
- OmniFocus 不像 Things 或者滴答清单那么，任务完成了之后就完全从列表内隔离开，而是继续保持原有的结构在穿插在其他未完成的项目中，导致界面很杂乱，虽然也可以通过改变视图为显示剩余，但这样又失去了结构，总之项目结构和整洁度二者只能去其一。
- 最主要的是产品的使用逻辑和我不对付，Things/滴答都有一个今日视图，给任务安排一个时间，他就会出现在那天的今日视图中，当然也可以通过 perspective 建立一个筛选过的今日视图（比如说筛选出`正在进行`标签或者有 defer/deadline date 是今日以及以前的任务。但我发现我就会滥用截止日期，过期的多了最后会导致对截止日期过期不敏感了，再加上杂乱的界面，会感觉失去重点和优先级，反而完成不了要紧事。

当然 OmniFocus 也有很多特别出彩的地方，比如说自定义 perspective（里面的条件很丰富），review 功能，插件自动化，Focus View（配合新窗口）等。具体可以见我之前的[文章](https://yinan.me/todo-app.html)。

## 滴答 vs OmniFocus

以下是我在会员免费期体验到的，有些功能可能免费版没有，另外限于时间，体验内容肯定不够完全。

### 优点：
- OmniFocus 和 things 的笔记一栏是长方形选中框的的下延展，随着笔记内容变多而变大，things 是纯文本格式， OmniFocus 是富文本，但是似乎只能通过粘贴保留格式，输入是纯文本格式，而且 OmniFocus 还挺卡的。滴答清单每一条任务展开之后占据右侧1/3窗口，完全可以当作一页纸来写（所以官方提供了转化为笔记的功能吧），还可以对内容进行加粗高亮，富文本。
- 操作和 Things 差不多顺滑，就是鼠标拖动支持的有点别扭（默认鼠标是选中文本，得选中左边的三条杠小图标才能拖动），目前来看键盘快捷键支持不如 Things 和 OmniFocus。
- 我挺喜欢他这个归档和完成的隔离的，眼不见为净，OmniFocus show all 的话会很乱，但是我又需要看到整个 project 的结构 （Things 的 logbook 完全就没有原来的 project结构了，或者说 things 本身就没有 task 结构(所有 task 都是平铺的，以下就只有 check item了，只有 heading ， heading 可以被 mark as complete，这样也挺好，所以在这种情况下，他的 heading 不是用来kanban 的，因为我需要知道 heading 下的某一种结构)
### 缺点
- 数据存储备份：OmniFocus 和 Things 似乎都是本地数据库+本地多副本备份+云端同步的方式，OmniFocus 支持手动打开 .ofocus-backup 回溯到某一个版本，然后支持本地覆盖云端/云端覆盖本地。滴答清单的数据好像都在云端存储，本地甚至不会显示出项目内所有已完成的任务（所以会在你搜不到东西的时候，有在云端中搜索的选项）
- 数据导出：滴答只支持任务导出到 csv，OmniFocus 支持导出 csv 和 .ofocus 文件，还可以不全部，选中筛选过某一些项目/任务单独导出。
- mac 软件的第三方支持：
  - Raycast: OmniFocus 没有，滴答很好用；Alfred: OmniFous > 滴答。
  - [Popclip](https://www.popclip.app/extensions/x/htd93q)
  - Chrome 插件，TickTick 会更加强大一点, OmniFocus 只有一个第三方的添加。
  - 全局添加：OmniFocus 有 Services - Add to OmniFocus 和 Share menu 两项。滴答和 Things 都是快捷键唤出一个类似于 spotlight 的窗口添加，things 和 OmniFocus 会有对当前窗口的 context 自动填充。
  - API 与自动化: 
    - Things 有 [URL scheme](https://culturedcode.com/things/support/articles/2803573/), [Applescript](https://culturedcode.com/things/support/articles/2803572/), [第三方 python api](https://github.com/thingsapi/things.py)还有官方提供的[捷径库](https://culturedcode.com/things/support/articles/2955145/).
    - OmniFocus 有 Applescript 和 Javascript 来实现插件。而且可以通过直接读取 sqlite 数据库自动批量的导出数据，之前根据此写过一个[导出到 markdown 的脚本](https://github.com/yinan-c/Omnifocus-export-markdown)。
    - 滴答和 TickTick 有 [OpenAPI](https://developer.dida365.com/docs#/openapi) 非官方 [ticktick-py](https://github.com/lazeroffmichael/ticktick-py) (可能需要自行修改所有域名到 dida365.com) 等。





## 滴答的其他功能

除了基本的 tasks，滴答还提供番茄钟和习惯打卡，不过目前我没有找到合适的导出这两部分数据的方案，所以没有深度试。

## 迁移工作

Things 到滴答的迁移好像挺顺滑的（没有深度试），如果是反过来目前 Things 官方没有支持，只能自己从 API 或者导出的 csv 里面想办法。

OmniFocus 到滴答导入过程需要在 OmniFocus 选中任务再导出 csv，而且导入之后会丢失创建和放弃任务的时间点(后者应该是 OmniFocus 的锅，因为同样的问题在你归档旧的已放弃任务的时候也会出现，会重新变成未完成状态并且丢失放弃时间戳)。

我之前写过[OmniFocus](https://github.com/yinan-c/Omnifocus-export-markdown) 以及 [Things](https://github.com/yinan-c/things2md) 导出 markdown 的脚本，也可以用已完成项目按时间规律生成回顾/周报的功能，也可以把所有的任务分项目导出 markdown。配合 git 还可以追踪项目的变化情况。

迁移之后，花了点时间用各种 API 实现了导出所有未完成/部分完成任务，增量缓存 json，保存 markdown，再输出为 RSS。
其实折腾这么多就是为了能够把数据主动权在自己手里，如果平台/工具倒闭了（希望不要）至少自己还有数据能有退路再保留一份纯文本供自己阅读。

## 最后留下两局话吧

关于 GTD（Get Things Done），完成事情是最终目的，折腾上花费的时间不如直接去完成你列表上的项目。这里引用一句话，
# TODO Focus is priority by 
关于工具，适合自己才是最好的。所以尽量秉承那句话 If it ain't broken, don't fix it.

## 相关

- [滴答清单/TickTick 官方API尝试](https://juejin.cn/post/7376484708547870731)
