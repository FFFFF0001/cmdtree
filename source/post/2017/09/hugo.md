---
date: 2017-09-05 13:18:53
title: 使用Hugo 搭建静态博客
category: 使用笔记
---

Hugo是一个用Go语言编写的，和Jekyll一样，都是静态博客生成系统，将markdown转换为静态网页。同样的，我们也可以将生成的网页托管到Github Pages。

# 安装 Hugo

官网介绍的安装方法是mac平台的，但是在其它平台安装也是非常简单的，我们只需要在 [Releases · gohugoio/hugo](https://github.com/gohugoio/hugo/releases)下载对应的版本：

1）Windows版本，下载ZIP压缩包

![](/pics/2017/09/Screenshot_20170905_133648.png)

然后将下载的压缩包解压至任意路径，再将此路径添加至系统环境变量`Path`即可，

![](/pics/2018/01/1201.png)

2）Linux平台就更加简单了，比Jekyll和Hexo都更加容易，对于大部分的发行版，都在官方源添加了Hugo，可以直接使用包管理器安装它们：

对于Ubuntu:

```
# apt-get install hugo
```
但是这样安装可以会安装到旧的版本，例如我在Ubuntu 16.04上直接安装，查询版本

```
$ hugo version
Hugo Static Site Generator v0.16-DEV BuildDate: 2016-02-07T01:14:17+08:00
```

安装到了0.16版本，所以我推荐到Github下载最新版本：[Releases · gohugoio/hugo](https://github.com/gohugoio/hugo/releases)

![](/pics/2017/09/Screenshot_20170905_131620.png)

可以直接下载deb包安装。

对于Archer，直接就可以安装到最新版本

```
# pacman -S hugo
$ hugo version
Hugo Static Site Generator v0.26 linux/amd64 BuildDate: 2017-08-07T18:27:14+02:00
```


# 如何使用

使用如下命令创建一个不包含主题的站点

```
$ hugo new site quickstart
```

目录结构

```
quickstart
├── archetypes
├── config.toml        ##配置文件
├── content            ##文章放置文件夹
├── data
├── layouts
├── static
└── themes             ##主题文件夹
```


进入到站点目录下并安装主题

```
$ cd quickstart
$ git init
$ git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
```

编辑配置文件，设置主题

```
$ echo 'theme = "ananke"' >> config.toml
```

## 创建一篇文章

```
hugo new posts/my-first-post.md
```

my-first-post.md 自动生成到了 content/my-first-post.md ，打开 my-first-post.md 看下：
```
+++
date = "2015-10-25T08:36:54-07:00"
draft = true
title = "about"

+++

正文内容

```

内容是 Markdown 格式的，+++ 之间的内容是 TOML 格式的，根据你的喜好，你可以查询官方文档换成 YAML 格式（使用 --- 标记）或者 JSON 格式。


OK～

## 运行站点

```
$ hugo server -D
Started building sites ...
Built site for language en:
0 draft content
0 future content
0 expired content
0 regular pages created
6 other pages created
0 non-page files copied
0 paginator pages created
0 categories created
0 tags created
total in 7 ms
Watching for changes in /home/rhatyang/Desktop/hugo-demo/quickstart/{data,content,layouts,static,themes}
Serving pages from memory
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop

```

打开浏览器，输入[http://localhost:1313/](http://localhost:1313/)，即可看到站点已经运行了

![](/pics/2017/09/Screenshot_20170905_140949.png)

# 部署

可以通过下面的命令生成静态页面

```
$ hugo --theme=hyde --baseUrl="http://YOURNAME.github.io/"
```

所有的静态文件会生成到public文件夹内，然后推送到仓库

```
$ cd public
$ git init
$ git remote add origin https://github.com/YOURNAME/YOURNAME.github.io.git
$ git add -A
$ git commit -m "first commit"
$ git push -u origin master
```

然后即可通过`YOURNAME.github.io`访问到站点啦。
