# How to let your shell to remember your commands

Whenever you got a new machine, there's always endless configurations porting, codes compilations and packages installations. It is crutial step to make the new machine meets your habits.

Recently, I got access to a new supercomputer for a limited amount of time, I started using it without much configuration. Soon I found myself missing the convenience of auto-suggestion for commands, which I got used to in prevously machines I've wored on.

Auto-suggestion in your shell is basically a plugin/extension that remembers your commands history and provide suggestions when you type in the first few letters of a command. When you find yourself frequently using the same commands (such as `ssh` to a specific server), it could be really useful.

This is how the suggestions will look like (I'm using zsh-autosuggestions here):

![](../output/pics/zsh.png)

So this article is mainly to give recommendations for both zsh and bash users on how to configure the shell to remember your commands.

## 1. zsh-autosuggestions for zsh

On my mac, zsh is the default shell, the plugin `zsh-autosuggestions` is what I want to recommend here. It suggests commands when you type in a zsh shell, and you can simply press the right arrow key to accept the suggestion.

To install it, you can follow the instructions on their [github repo](https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md). You can use Antigen, Oh My Zsh, Homebrew or manually install it.

I use oh-my-zsh for managing my zsh configurations. Actually I'm using a rather minimal configuration of oh-my-zsh, which consists only 2 plugins. These are the lines to configure oh-my-zsh in my `~/.zshrc`:

```bash
export ZSH="$HOME/.oh-my-zsh"
ZSH_THEME="alanpeabody"
plugins=(git zsh-syntax-highlighting zsh-autosuggestions)
source $ZSH/oh-my-zsh.sh
```
As you can see, to install `zsh-autosuggestions` you just need to add it to the `plugins` list, separated by a space, tab, or newline.

There are definitely more to explore in oh-my-zsh, but I'm not going to talk about them in detail here. If you're interested in more configurations, you can always check out the [official website](https://ohmyz.sh/) or their [github repo](https://github.com/ohmyzsh/ohmyzsh).

> (PS. I also recommend [pure](https://github.com/sindresorhus/pure) as a beautiful and minimal ZSH prompt theme, and it is developed and maintained by my favorite open source and mac apps developer Sindre Sorhus.)

## 2. ble.sh for bash

For some linux machines, bash is default shell. If you are using bash, I would recommend [ble.sh](https://github.com/akinomyoga/ble.sh), which stands for Bash Line Editor.

I was looking for a way to let my bash shell to remember my commands, and I found there is a [oh-my-bash](https://github.com/ohmybash/oh-my-bash) repo, which is the counterpart of oh-my-zsh, for managing your bash configuration. However, I couldn't find a easy-to-use auto-suggestion plugin that can be installed via oh-my-bash.

Then I found [ble.sh](https://github.com/akinomyoga/ble.sh), and you can even try it first without installation.
    
```
git clone --recursive --depth 1 --shallow-submodules https://github.com/akinomyoga/ble.sh.git
make -C ble.sh
source ble.sh/out/ble.sh
```

Then try typing in a few commands, you'll find it achieves the same functionality as `zsh-autosuggestions`, it even gives suggestions on commands that you never used before.

If you like it, you can quickly install it via running the following command:

```
git clone --recursive --depth 1 --shallow-submodules https://github.com/akinomyoga/ble.sh.git
make -C ble.sh install PREFIX=~/.local
echo 'source ~/.local/share/blesh/ble.sh' >> ~/.bashrc
```

I hope some of you will find this article useful, and I'm also looking forward to hearing your recommendations on other useful plugins or your shell configurations.