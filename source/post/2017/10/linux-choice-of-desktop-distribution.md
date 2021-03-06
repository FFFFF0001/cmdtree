---
title: Linux桌面发行版的选择
date: 2017-10-19T10:37:48+00:00
category: Unix/Linux
---

基于Linux的发行版有很多，有广泛运用于网站服务器的CentOS，也有在桌面Linux中独占半边天的Ubuntu，现在来说说如何选择一个最适合自己的发行版。顺便推荐一个网站，里面有各种Linux发行版的最新资讯以及热度排行[DistroWatch.com: Put the fun back into computing. Use Linux, BSD.](http://distrowatch.com/)

![](/pics/2017/10/1901.jpg)

## 考虑条件

主要谈谈选择一个桌面发行版应该考虑的一些方面：（缺省）

### 内核版本

linux内核不能太旧，对于较新的CPU（如第七代CPU）使用4.10以下内核可能会出现功耗占用过多的情况，可能会导致：发热、耗电、性能损耗。

例如CentOS作桌面就不是很好，最新的CentOS的内核也才3.10，当然你也可以自己升级内核，这个我们不讨论。

### 软件包数量

作为一个桌面发行版，软件包的数量一定不能少，在这方面表现的最好的肯定是Arch Linux（based），默认的软件源加上AUR和archlinuxcn秒杀一切其它发行版了。

比较差一点的就是openSUSE了，由于其版权控制严重，默认源可以说啥都没。

折中的就是Debian系的了，跟archlinux比差不了多少，但是有些只提供源码的程序只能选择编译。

### 桌面

其实这块考虑的因素不是占比太重，**但是却是最值得说的**。

对于有点经验的用户选个自己最喜欢的就好了，但是如果你有选择恐惧症或者你不知道你中意哪个，我建议在GNOME和KDE中选一个，因为这两个桌面的使用人数和社区都比其它的要庞大的多。

这二者相比来说GNOME的出错率更高，以往大部分的archlinux用户在“滚挂”的时候，是除了驱动问题之外的最大罪魁祸首了，目前最新版本为3.26.1，我已知的现在只有archlinux和openSUSE Tumbleweed已经更新到此版本，而且我在之前就是因为更新了最新版本导致问题太多已经换到KDE了，也有很多人都反应有此情况

![](/pics/2017/10/1904.jpg)

但是对于其它不是很激进的发行版我是推荐gnome的（例如Debian、openSUSE Leap），毕竟Gnome可以说的上是Linux的一个标签吧（许多发行版的缺省桌面）。

如果说是性能较低的电脑就比较推荐cinnamon或者xfce，这两者在linux mint或者debian中都可以选择。

![](/pics/2017/10/1903.png)

### 易用性

这一块是为不想折腾的或者不是很有经验的用户说的

易用性主要体现在：驱动配置、桌面配置（字体、输入法）等方方面面，在这方面做得比较好的有Ubuntu、Linux mint、manjaro。Ubuntu推荐LTS版，mint基于Ubuntu lts，这两者的社区都是非常活跃的（mint问题直接搜Ubuntu即可）。manjaro基于archlinux，可以理解成一个打包好的archlinux，即开即用，软件包数量多，滚动更新等特点。

### 发行模式

无外乎两种：Fixed（固定版本号）、Rolling（滚动更新，以日期号作为版本号）。

大部分的发行版都是采用固定版本号的形式发行，如Fedora 27、Ubuntu 17.10等。

以Rolling形式发行的主要有archlinux、openSUSE Tumbleweed，这两者对比来说openSUSE tw更加激进，但是openSUSE默认使用btrfs文件系统，加上其独有的Yast中的独一无二的snapper管理足以上你滚起来无后顾之忧，更何况openSUSE一直以稳定性著称。

## 推荐发行版

对比完了还是要推荐一下的：

![](/pics/2017/10/1902.jpg)

在各方面表现良好的是**Ubuntu LTS**（目前最新16.04），使用Unity桌面，可自行更换gnome桌面，内核为4.10，可以使用backports源更新内核，软件包多，驱动方便，即开即用等特点。缺点：基于内核错误。

**Arch Linux**：优点太多，不一一列举，只谈缺点：不能即开即用，什么都得自己配置。。。好像想不到什么缺点了。其实那个唯一的缺点也是一个优点，结合archwiki可以让你更加熟悉linux系统**。大多数人经常谈到的“滚挂“在我看来是不存在的**，即使有也只是极小概率事件，大部分原因出在驱动和桌面，至于这二者已经不是什么问题了，用arch live arch-chroot上去删除即可。

### 最后

我在上面提到我只谈缺省，**因为任何一款发行版只要你有时间和精力都可以调教到十分易用**，我并没有歧视任何一款发行版的意思噢。