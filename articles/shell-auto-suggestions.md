# How to let your shell to remember your commands

Whenever you got a new machine, it means endless porting configurations, compilation of codes and installation of packages to let it be usable for you.

Recently, I got access to a new supercomputer for a limited amount of time, so I start using it without much configuration. Soon I found myself missing the convenience of auto-completion and auto-suggestion of my shell, which I got really used to in any other machines I used.

What shell auto-completion and auto-suggestion do is to remember your commands and give you suggestions when you type in the first few letters of a command. When you find yourself typing the same commands over and over again (such as `ssh` to a specific server), you'll find it really useful.

This is how the suggestions will look like (I'm using zsh-autosuggestions here):

![](../output/pics/zsh.png)

So this article is mainly about giving recommendations for both zsh and bash users on how to let the shell to remember your commands.

## 1. zsh-autosuggestions for zsh

On my mac, zsh is the default shell, 

The plugin `zsh-autosuggestions` is the one I want to recommend here. As the name suggests, it gives you suggestions for commands when you type in a zsh shell, and you can simple press the right arrow key to accept the suggestion.

To install it, you can follow the instructions on their [github repo](https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md). You can use Antigen, Oh My Zsh, Homebrew or manually install it.

I use oh-my-zsh for managing my zsh configuration. Actually I adopt a minimal configuration of oh-my-zsh, which is just 2 plugins. These are the lines to configure oh-my-zsh in my `~/.zshrc`:

```bash
export ZSH="$HOME/.oh-my-zsh"
ZSH_THEME="alanpeabody"
plugins=(git zsh-syntax-highlighting zsh-autosuggestions)
source $ZSH/oh-my-zsh.sh
```
As you can see to install `zsh-autosuggestions` you just need to add it to the `plugins` list, separated by a space, tab, or newline.

There are definitely more to explore in oh-my-zsh, but I'm not going to talk about them in detail here.

If you're interested in more configurations, you can check out the [official website](https://ohmyz.sh/) or their [github repo](https://github.com/ohmyzsh/ohmyzsh).

> (PS. I also recommend [pure](https://github.com/sindresorhus/pure) as a beautiful and minimal ZSH prompt theme, and it is developed and maintained by my favorite open source and mac apps developer Sindre Sorhus.)

## 2. ble.sh for bash

For some linux machines, bash is default shell. If you are using bash, I would recommend [ble.sh](https://github.com/akinomyoga/ble.sh).

I was looking for a way to let my bash shell to remember my commands, and I found there is a [oh-my-bash](https://github.com/ohmybash/oh-my-bash) for managing your bash configuration, but I couldn't find a easy-to-use auto-suggestion plugin that can be easily installed via oh-my-bash.

Then I found [ble.sh](https://github.com/akinomyoga/ble.sh), you can try it first without installation.
    
```bash
# TRIAL without installation
git clone --recursive --depth 1 --shallow-submodules https://github.com/akinomyoga/ble.sh.git
make -C ble.sh
source ble.sh/out/ble.sh
```
Then try typing in a few commands, you'll find it achives the same functionality as `zsh-autosuggestions`, it also give suggestions for commands that you never used before.

If you like it, you can quickly install it via running the following command:

```bash
# Quick INSTALL to BASHRC

git clone --recursive --depth 1 --shallow-submodules https://github.com/akinomyoga/ble.sh.git
make -C ble.sh install PREFIX=~/.local
echo 'source ~/.local/share/blesh/ble.sh' >> ~/.bashrc
```

I hope some of you will find this article useful, and I'm also looking forward to hearing your recommendations on other useful plugins or your configurations for your shell.