# 从WSL开始你的Linux之旅

文章：**@CoraBlack**  
图片提供：**@chang459 @CoraBlack @CoreSheer**

入门Linux，我们首先需要一个适合入手的Linux发行版，最无痛的选择，自然是WSL（Windows下的Linux子系统）。在早期的入门指南中，我们将以WSL作为主要的系统平台，带你一步步走进Linux世界，后期，我们再转向完整的操作系统，尝试将Linux完美嵌入你的生活与工作中

## 什么是WSL

WSL是微软为Windows平台开发的Linux子系统，具有低性能损耗，简易的硬件直通和方便的跨文件系统交流的特点。设计初衷是为了让开发人员能够同时使用Windows和Linux的强大功能，为双系统的使用免去了较高的性能开销代价

> ### 使用WSL的先决条件
>
> 1. 必须运行 Windows 10 版本 2004 及更高版本（内部版本 19041 及更高版本）或 Windows 11 才能使用WSL。
> 2. 我们需要在**启用或关闭Windows功能**系统选项卡中将```Hyper-V虚拟机平台```与```适用于Windows的Linux子系统```两个关键功能勾选上。在旧一点的Windows上还可能会有```虚拟机平台```的选项，勾选即可。点击```确定```后，可能会需要你重新启动电脑，如果没有在进行重要的工作，那么可以立刻重启你的电脑以应用新功能。
>
> ![EnableHyperVService](../../Images/QuickStart/GoodBeginningWithWSL/EnableHyperVService.jpg)
> ![EnableWslService](../../Images/QuickStart/GoodBeginningWithWSL/EnableWslService.jpg)
>
> 3. Suggestion：建议去微软商店中搜索并下载```Windows Terminal```。这个软件能帮你管理WSL和其他终端界面（还可以美化你自己的终端界面，看起来就更专业doge）
>
> ![WindowsTerminalInMS](../../Images/QuickStart/GoodBeginningWithWSL/WindowsTerminalInMS.jpg)

## Linux发行版（Linux distro）

首先，我们需要了解一个概念，Linux不是一个操作系统，而是一个系统内核
> 系统内核仅包括系统最基础的部分，比如：IO驱动，硬件调度，文件系统等等  
> 这好比一栋建筑的地基，地基是不能直接投入使用的，必须要有美丽的地板，美丽的墙面……只有这些才能组成一栋完美的建筑，并投入使用。

一个完整的操作系统，除了需要有内核，还需要有**用户层面**的软件支持（桌面环境，基础软件，驱动等等周边软件），这样才能构成一个可用的操作系统  
我们学习Linux系统前，我们应该需要一个合适的发行版，我们希望它比较**好上手**，**对用户比较友好**，而且它应该有**健全丰富的社区**，在我们遇到问题时更容易找到解决方案  
在本篇学习中，我们将从 **Ubuntu（乌班图）** 作为各位企鹅们的Linux旅途的第一站  

## 开始安装WSL（Linux之旅，开始！）
>
> ### 你可以使用两种方式获取所需的WSL发行版
>
> - 通过微软商店下载
> - 使用命令行在线下载获取

## 从**Microsoft Store**获取WSL发行版

**Warning**：不推荐该方法安装，可能会遇到奇奇怪怪的问题，但是可以获得更好的网络下载环境。整体上说，我依然推荐[使用命令行安装WSL](#从命令行获取wsl发行版)。（你猜他为什么评分3.9）

首先，打开电脑中微软商店，搜索Ubuntu并找到相应的软件,进入详情页并点击获取按钮便可开始下载获取（就是如此简单～～～）。

![微软商店中的Ubuntu](../../Images/QuickStart/GoodBeginningWithWSL/UbuntuInMS.jpg)

**Warning**：如果点击开始菜单中的Ubuntu应用图标，可能会遇到注册发行版失败导致的各种奇怪问题，所以我的建议是，在使用WSL前先[检查WSL的安装情况](#wsl的初始化工作)。

## 从命令行获取WSL发行版

**Warning**：进行使用命令行安装可能会遇到网络问题，建议备好魔法

首先，在你完成以上的前置步骤后，打开终端，输入以下命令

```powershell
# 获取在线可用的全部发行版选项  
wsl --list --online
```

在这一步中，若你先前没有使用过WSL的经历，那么wsl会自动下载最新的稳定版系统内核，这个下载速度取决于你的网络环境，还是那句话，必要的```魔法```还是需要的  
如果你的网络没有什么问题，你会在终端中看见可用的发行版列表  

![ListWslDistro](../../Images/QuickStart/GoodBeginningWithWSL/ListWslDIstro.jpg)

接下来，我们需要关注```NAME```一栏，并使用以下命令安装需要的Linux发行版

```powershell
# 安装WSL发行版
wsl --install <distro_name>
# 安装Ubuntu为例
wsl --install Ubuntu
```

等待读条完毕后，没有显示错误信息，那么我们安装WSL的步骤便结束了

## WSL的初始化工作

我知道你已经迫不及待的想要欣赏一下这个神秘又强大系统的真颜。不过，在此之前，我们需要检查我们所下载的WSL发行版是否注册成功

```powershell
# 列出已安装的可用的WSL发行版
wsl --list
```

![InstalledDistroList](../../Images/QuickStart/GoodBeginningWithWSL/InstalledDistroList.jpg)

如果你能在列出信息中找到```Ubuntu```的相关信息，那么就说明你已经安装并注册成功了  
接下来，我们就可以打开我们的Ubuntu系统了

```powershell
# 进入默认的WSL系统
wsl
```

安装新系统后，它会开始进行初始化操作，这个过程是全自动的，不需要你去干预  
如果一切运行正常，那么它将会提示你输入你的```Unix user account```，这个将会成为你的Linux系统默认用户的用户名  

![InputUnixName](../../Images/QuickStart/GoodBeginningWithWSL/InputUnixName.jpg)

> Linux用户名需要满足以下要求：
>
> 1. 不能出现大写字母
> 2. 不能有空格与特殊字符

输入用户名后，它还会提示你输入你的用户密码（这个密码非常重要不能忘记，忘记Linux的密码就几乎等于失去了对电脑的控制权，行动很受限，几乎只能通过重装系统来恢复你的正常使用了）  

> **Warning**：在输入密码过程中界面上不会有任何反应，但实际上已经输入成功，该措施是旨在防止别人偷看你的密码，是一种安全措施。后续使用过程中需要使用密码也是一样的。

设置完初始用户后，正常来说，你便能看见处于你所创建的用户下的命令提示符了  

![CMD](../../Images/QuickStart/GoodBeginningWithWSL/CMD.jpg)

这么值得庆祝的时刻，不如……我们来玩点酷酷的（doge）？  

我们先来输入一些看起来就很高级的命令

```bash
# 更新软件仓库
sudo apt update

# 更新已安装的软件包
sudo apt upgrade
```

> 这里简单介绍一下这些命令  
> ```sudo```：s用以管理员权限执行某个命令，Linux下的管理员是一个用户名为root的用户，root用户非常强大，它有完全掌握LInux系统的能力，是一个既危险又强大的存在！  
> ```apt```：apt你可以理解为是一个基于命令行操作的应用商店。但是它是一个包管理器，它比我们常规认识的软件商店可强大的多！每个发行版有着不同的官方包管理器，在Debian系Linux中，apt便是默认的包管理器  
> ```update```和```upgrade```的作用看上述的注释即可(Yeah~!)。但需要注意的是，他们是apt的命令，而不是单独的命令。

好吧，我们现在使用apt包管理器安装第一个软件吧！  
首先，我们先来了解apt的安装命令是什么

```bash
sudo apt install <package>
```

如果你了解过Linux社区，那么你一定听过一句话：**有事没事都```fetch```一下**。

```bash
# 我们也来fetch一下
sudo apt install neofetch
```

安装好后，我们现在这么乱糟糟的命令行界面看着都烦，我们先来清理一下

```bash
# 清屏
clear
```

然后（doge）

```bash
# Fetch!!!!!!!!!!!!!!!!!!!!
neofetch
```
![Neofetch](../../Images/QuickStart/GoodBeginningWithWSL/NeoFetch.jpg)

恭喜你！你已经正式踏入Linux殿堂的大门了，你已经成为万千企鹅大家庭的一员。  
Linux世界，就交给你去慢慢探索啦！

[传送门->Next Page](./BasicCommand.md)