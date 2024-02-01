# 如何让 Shell 记住常用命令

每当配置一台新服务器时，迁移配置、编译代码和安装包，都是最一开始要做的事情。
最近，我们组有了一台新的超算，但给的时间有限，于是我几乎没有配置，登录上编译完软件包就开始用了。然而，在我一而再再而三重复输入类似的命令后，我发现自己已然适应，甚至完全离不开命令自动补全带给我的便利了。

Shell 自动建议是在你输入一条命令的前几个字母时，从命令行历史中给出补全建议。如果你需要经常输入相同或类似的命令时（例如，ssh到特定的服务器），那么这个功能会非常有用，如下图所示：

![](../output/pics/zsh.png)

因此，本文主要是给 zsh 和 bash 用户推荐 Shell 记住常用历史命令的插件，以及如何安装和配置它们。

## 1. ZSH 用户：zsh-autosuggestions

在 Mac 上，zsh 是默认的 shell，我推荐使用 `zsh-autosuggestions` 插件。如其名，它会在你输入 zsh 命令时自动给出建议，然后按右箭头键接受建议。

可以按照其 [github repo]((https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md)) 上的说明进行安装，安装方式有 Antigen、Oh My Zsh、Homebrew 或手动安装。

我使用的是 oh-my-zsh 来管理 zsh 配置，这是我在 `~/.zshrc` 中有关 oh-my-zsh 的代码，我目前使用得很简单，只有两个插件：

```
export ZSH="$HOME/.oh-my-zsh"
ZSH_THEME="alanpeabody"
plugins=(git zsh-syntax-highlighting zsh-autosuggestions)
source $ZSH/oh-my-zsh.sh
```

可以看到安装方式十分简单，只需把 `zsh-autosuggestions` 加入到 `plugins` 列表中，用空格、制表符或换行符分隔不同的插件即可。

当然，oh-my-zsh 还有很多其他可玩的地方，不管是主题还是插件，这里就不详细介绍了。如果你对更多配置感兴趣，可以查看 [官方网站](https://ohmyz.sh/) 或他们的 [github repo](https://github.com/ohmyzsh/ohmyzsh)。

> （PS. 另外我还推荐 [pure](https://github.com/sindresorhus/pure) 作为一个漂亮而简洁的 ZSH 提示符主题，它也是我最崇拜的开源和 Mac 应用程序开发者 Sindre Sorhus 开发维护的。）

## 2. BASH 用户：ble.sh

对于一些 Linux 机器，bash 是默认的 shell。如果你使用 bash，我推荐 [ble.sh](https://github.com/akinomyoga/ble.sh)。

我在寻找让 bash 记住常用命令的方法时，发现了 [oh-my-bash](https://github.com/ohmybash/oh-my-bash)，和 oh my zsh 对应，它可以用来管理 bash 配置，但我没有找到一个可以通过它轻松安装的 auto suggestions 插件。

然后我发现了 ble.sh，它甚至提供了试用命令，你可以不用安装的情况下暂时使用它，只需运行以下命令：

```
git clone --recursive --depth 1 --shallow-submodules https://github.com/akinomyoga/ble.sh.git
make -C ble.sh
source ble.sh/out/ble.sh
```

当你尝试输入一些命令，你会发现它和 `zsh-autosuggestions` 的基本功能是一样的，甚至会给出你从未使用过的命令的建议。

如果你喜欢它，当然也可以通过运行以下命令快速安装：

```
git clone --recursive --depth 1 --shallow-submodules https://github.com/akinomyoga/ble.sh.git
make -C ble.sh install PREFIX=~/.local
echo 'source ~/.local/share/blesh/ble.sh' >> ~/.bashrc
```

希望本文对你有用，也期待听到你对其他插件或 shell 配置的建议。