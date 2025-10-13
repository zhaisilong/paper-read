---
{"dg-publish":true,"permalink":"/tutorial/oh-my-zsh/"}
---

# Oh My Zsh 安装与配置教程

![](https://cdn.molastra.com/weixin/2025/08/8786999d66f60764258e713e3c24cc80.png)

`Zsh`（Z shell）是一款功能强大且高度可定制的 shell，配合 `Oh My Zsh` 框架可以极大提升终端的使用体验。本教程将带你一步步完成 `Zsh` 及 `Oh My Zsh` 的安装、常用插件的配置，以及流行主题 `Powerlevel10k` 的使用，适用于主流 `Linux` 发行版及 `MacOS`。

你将学会如何：

- 安装 `Zsh` 并切换默认 `shell`
- 安装` Oh My Zsh` 框架
- 安装并配置实用插件，如自动建议和语法高亮
- 使用 `Powerlevel10k` 打造漂亮且功能丰富的终端提示符
- 保持 `Oh My Zsh` 的更新和管理

无论你是刚接触 `Zsh`，还是想打造一个高效美观的终端环境，这份教程都能帮你快速上手。

## 1 安装 Zsh

根据不同发行版选择合适命令：

- Arch Linux:

```bash
yay -S zsh
```

- Ubuntu / Debian:

```bash
sudo apt-get update
sudo apt-get install zsh
```

- CentOS (可参考上面链接安装)
- MacOS (自带 `zsh`  可通过下面的命令检测)

```bash
cat /etc/shells
```

## 2 安装 Oh My Zsh

```bash
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```

或者使用 `curl`：

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## 3 安装常用插件

- **zsh-autosuggestions**：命令自动建议
- **zsh-syntax-highlighting**：命令语法高亮
- **zsh-completions**：补全插件
- **powerlevel10k**：美观主题

### 3.1 使用包管理器安装插件

- Arch Linux:

```bash
yay -S zsh-autosuggestions zsh-syntax-highlighting zsh-theme-powerlevel10k zsh-completions
```

- Ubuntu / Debian (系统仓库版本可能不是最新，powerlevel10k 需手动安装):

```bash
sudo apt-get install zsh-autosuggestions zsh-syntax-highlighting
```

### 3.2 手动安装插件（推荐最新版）

```bash
# ZSH_CUSTOM=${ZSH_CUSTOM:-~/.oh-my-zsh/custom}

git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-completions $ZSH_CUSTOM/plugins/zsh-completions
```

## 4 配置

### 配置 Powerlevel10k 主题

编辑 `~/.zshrc` 文件，添加或修改如下内容(以 `Ubuntu` 为例)：

```bash
git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k

vim ~/.zshrc

# 然后设置 ~/.zshrc 中的变量 ZSH_THEME
ZSH_THEME="powerlevel10k/powerlevel10k"

# 并在 ~/.zshrc 最后名加入
source /usr/share/zsh-autosuggestions/zsh-autosuggestions.zsh
source /usr/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

如果手动安装了插件，确保添加 `source` 语句：

```bash
source $ZSH_CUSTOM/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh
source $ZSH_CUSTOM/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
# powerlevel10k 主题自动加载，无需额外 source，除非你的 oh-my-zsh 版本特别旧
```

第一次运行 `zsh` 时会自动提示配置，也可以手动启动：

```bash
p10k configure
```

## 5 设置默认 shell 为 zsh

```bash
chsh -s $(which zsh)
```

然后重新登录或重启终端。

## 7 Arch Linux 特别提示

如果你通过包管理器安装插件，某些插件可能位于：

```bash
/usr/share/zsh/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh
/usr/share/zsh/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
/usr/share/zsh-theme-powerlevel10k/powerlevel10k.zsh-theme
```

可以在 `~/.zshrc` 末尾添加：

```bash
source /usr/share/zsh/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh
source /usr/share/zsh/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
source /usr/share/zsh-theme-powerlevel10k/powerlevel10k.zsh-theme
```

## 8 更新 Oh My Zsh

```bash
omz update
```

## 9 额外建议

- 安装 Powerline 字体，以支持 Powerlevel10k 显示完整图标
- 详细主题配置参考 Powerlevel10k 文档: https://github.com/romkatv/powerlevel10k
- Oh My Zsh 官方链接: https://github.com/ohmyzsh/ohmyzsh.git

