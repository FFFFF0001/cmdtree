---
date: 2017-12-22 11:08:42
title: CSS框架——bulma
category: 学习笔记
---

又是闲得无聊，把博客重新写了一遍，刚开始使用的bootstrap框架，也是做出了现在这个样子，但是感觉不怎么好看，所以又找了找其它框架，然后就找到了这个——[Bulma](https://bulma.io/)，看了看还不错，就用它把主题重新写了一遍，下面说说我是如何使用这个框架的：

## 布局

首先应该先把网站的整体结构先布置好，像我这个博客的话，就会需要一个顶部`nav`、底部的`footer`、中间的部分根据情况是单栏还是双栏则需要加个`sidebar`。

![](/pics/2017/12/2201.png)



我这里先以单栏为例，则得到的HTML结构是这样的：

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Hello Bulma!</title>
</head>
<body>
  <nav class="navbar">
    <!-- nav -->
  </nav>
  <section class="section">
    <!-- content -->
  </section>
  <footer>
    <!-- footer -->
  </footer>
</body>
</html>
```

### navbar

绝大多数的网站都需要一个顶栏，`navbar`就是bulma的一个组件，一个navbar分为两部分，`navbar-brand`和`navbar-menu`，navbar-brand为整个网站的Title或者LOGO。

![](/pics/2017/12/2202.png)

```html
<nav class="navbar" role="navigation" aria-label="main navigation">
  <div class="navbar-brand">
    <!-- navbar items, navbar burger... -->
  </div>
  <div class="navbar-menu">
    <!-- navbar start, navbar end -->
  </div>
</nav>
```

navbar-menu在移动端中会隐藏起来，可以通过一个按钮来点击显示，这就需要在navbar-brand中添加一个button

```html
<button class="button navbar-burger" data-target="navMenu">
  <span></span>
  <span></span>
  <span></span>
</button>
```

因为bulma不包含js代码，所以这段代码需要自己来写了，官网也给了一个例子，其实很简单，如果使用了JQuery的话：

```js
$(document).ready(() => {
  $(".navbar-burger").click(() => {
    $(".navbar-menu").toggle();
  })
})
```

navbar-menu分为`navbar-start`和`navbar-end`其中一个居左一个居右

```html
<div class="navbar-menu">
  <div class="navbar-start">
    <!-- navbar items -->
  </div>

  <div class="navbar-end">
    <!-- navbar items -->
  </div>
</div>
```

而navbar上面的项目只需要添加一个样式`navbar-item`类即可。

```html
<div class="navbar-start">
  <a class="navbar-item">
    Home
  </a>
</div>
```

navbar默认白色，可以更换颜色，具体可以使用的样式有`is-primary`、`is-link`、`is-info`、`is-success`、`is-warning`、`is-danger`、`is-black`、`is-dark`、`is-light`、`is-white`

效果如图所示：

![](/pics/2017/12/2203.png)

关于`navbar`的更多内容可以查看[Navbar | Bulma: a modern CSS framework based on Flexbox](https://bulma.io/documentation/components/navbar/)。


### section

bulma使用`section`来区分不同的模块，即在nav和footer中间的内容应该为一个section或者多个section，而且使用`.section`样式。

### container

在bulma中，无论在`navbar`、`section`、`footer`中，都需要立即放一个class为`container`的div，来让内容居中显示。

### content

这个class类至关重要，因为在bulma中，除了在这个类之外的所有文本都是一样的大小，所以在文章主体中必须添加这个类，当然很简单的方法就是像我这样在section中直接加上这个类就好了。

### footer

footer作为页面的页脚，添加一个class为`footer`的footer标签即可，`footer`类的样式为

```css
.footer {
    background-color: whitesmoke;
    padding: 3rem 1.5rem 6rem;
}
```

比较大。

关于更多布局的方法可以参考我博客的样式和[bulma](https://bulma.io)官网的样式。


## 响应式

Bulma 的网格体系基于 Flex 布局。需要使用`columns`来指定容器，使用`column`指定项目。

bulma和bootstrap一样，都支持12网格体系，你可以像这样来表示

- is-2
- is-3
- is-4
- is-5
- is-6
- is-7
- is-8
- is-9
- is-10
- is-11

或者你可以像我一样使用分数表示：

- 四分之三：is-three-quarters
- 四分之一： is-one-quarter
- 三分之二：is-two-thirds
- 三分之一：is-one-third
- 二分之一：is-half
- 五分之四：is-four-fifths
- 五分之三：is-three-fifths
- 五分之二：is-two-fifths
- 五分之一：is-one-fifth

具体使用实例：

```html
<div class="container">
  <div class="columns">
    <div class="column is-two-thirds">content</div>
    <div class="column is-one-third">sidebar</div>
  </div>
</div>
```

例如在我的主页中，左侧的文章列表使用了`is-two-thirds`，右边的sidebar使用了`is-one-third`，这与使用`is-9`、`is-3`的效果是一样的，也等同于bootstrap中的`col-md-9`和`col-md-3`。

![](/pics/2017/12/2204.png)

## 自定义

因为下载的bulma压缩包里带有sass源文件，而Jekyll默认就支持编译SASS，所以我直接引用的源码包里的sass文件，再把一些没用到的组件注释掉，省了差不多一半的大小。

使用Node构建项目时参考[Customize Bulma Bulma: a modern CSS framework based on Flexbox](https://bulma.io/documentation/overview/customize/)

## 参考&&推荐浏览

- [Get started with Bulma Bulma: a modern CSS framework based on Flexbox](https://bulma.io/documentation/overview/start/)

- [CSS 框架 Bulma 教程 - 阮一峰的网络日志](http://www.ruanyifeng.com/blog/2017/10/bulma.html#%E7%BD%91%E6%A0%BC%E4%BD%93%E7%B3%BB)
