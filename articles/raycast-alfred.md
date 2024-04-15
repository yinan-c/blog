# 如何只用一个 Escape 键退出 Raycast - Get the Best of Both Worlds with Raycast and Alfred

这篇文章主要想分享两件事，一是如何让 Raycast 能像 Alfred 一样只用一个 Escape 键退出搜索窗口，而不是每次摁一次只能一级一级得退出，二是如何利用 Deeplink 来同时使用 Raycast 和 Alfred， 发挥各自的优势。

## TLDR

利用这个 [Keyboard Maestro macro](../output/pics/remap_escape_in_Raycast.kmmacros) 实现在 Raycast 搜索窗口中 remap a single escape to multiple escape keys。

## 如果你还想听我唠叨

我不想讨论孰优孰劣，哪个是 mac 上最好用的 Launcher (LaunchBar:?)，也并不希望任何一个产品被挤压到退市，并且市场上良性竞争促使产品进步是对消费者有益的。

在我的电脑上两个都装了（感谢最早让我深度体验 launcher 的 Raycast），但是目前为止还是主要在使用 Alfred，仅仅是因为能够一键呼出和退出搜索窗口，强大的 Universal Actions，更快地文件搜索和 Navigation（每次1对1老板都惊艳于我找文件的速度:D），并且我也写了几个 [Alfred Workflow](https://yinan.me/my-open-source.html)。

但是 Raycast 也有很多优点，就比如同一个功能，eject disks, 我更偏向于 Raycast 的 hud 通知，而不是 Alfred 的系统通知（因为经常开着勿扰模式），另外比如 Show Desktop 这个 Raycast 内置插件，我并没有在 Alfred 社区找到合适的方案。如果你想要主要使用 Raycast，但也有这个烦恼， 那么你可以通过 Keyboard Maestro 设置一键退出 Raycast，如果你想要同时使用两个 Launcher，那么你可以利用 Deeplink 来实现。我会分别在下面两节讨论。

![](../output/pics/hud.png)

### 设置一键退出 Raycast

Raycast 有多级菜单，每次按 Escape 键只能退出一级，这是他们产品的特有设计，但确实大大减慢了我使用 Launcher 的速度。要实现一键退出多级菜单，Raycast 内置 Command + Escape 来回到主菜单，但是不会退出窗口（搜索完，还想让你继续搜索？），你仍然需要再次按下 escape 键才能退出。

之前用过 Keyboard Maestro 映射轻按 command + W 到 长按 command + W 来防止误关窗口，所以我想到了用 Keyboard Maestro 来实现映射一个 Escape 键到多个 Escape 键，关键问题在于如何识别 Raycast 的搜索窗口正在最前。好在已经有人在论坛上讨论过并且给出了[解决方案](https://forum.keyboardmaestro.com/t/solved-check-whether-raycast-is-running/29073/5)，我稍微修改了一下，实现了 remap，[下载地址在这儿](../output/pics/remap_escape_in_Raycast.kmmacros)。

### Deeplink: raycast:// 和 alfred:// 实现互相呼出

Raycast 和 Alfred 都支持 Deeplink，Raycast 中选中 command 摁下 Command + K，就可以看到 Copy Deeplink 的选项，然后你可以创建一个 Alfred Workflow 在打开这些 Raycast DeepLink 实现直接调用 Raycast command （并且整个过程 Raycast 窗口不会出现）

![](../output/pics/raycastdeeplink.png)

![](../output/pics/alfredworkflow.png)

同样地，而如果你想要在 Raycast 或者 keyboard Maestro, Shortcuts 等其他地方调用 Alfred workflow，Alfred 提供了 External Actions 来实现通过 Deeplink 或者 AppleScript 调用 Alfred 的 workflow。在 Raycast 中设置 Quicklinks 打开这个 URL 即可以实现调用 Alfred Workflow。

![](../output/pics/alfreddeeplink.gif)


