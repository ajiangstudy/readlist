> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.zhihu.com](https://www.zhihu.com/question/299390628/answer/2495155944)

> 更新一下------------------------有一些朋友说README写好了，但是没有代码特意写了一个js工具函数库,照…

![](https://pic1.zhimg.com/v2-afc92daf4c8da86932b1c5273b840fba_l.jpg?source=1940ef5c)董员外​

更新一下 ------------------------

有一些朋友说 README 写好了，但是没有代码

特意写了一个 js 工具函数库, 照着步骤一步一步的搭建

代码这不是有了嘛！！！！

还能写到简历上 ^_^

[董员外：如何手写一个 js 工具库并发布到 npm 上，别人能下载引用？1 赞同 · 4 评论文章![](https://pic3.zhimg.com/v2-79f5e2c3b3dc7c7f11a51667678bfef2_180x120.jpg)](https://zhuanlan.zhihu.com/p/543227065)

以下是原文内容 ------------------

经常逛 gitHub 就会发现，有很多用户的介绍页面花里胡哨的各种 GitHub 数据卡片和徽章，今天就跟大家分享一下，这些东西怎么做！

![](https://pic1.zhimg.com/v2-a665f98e5da618666bab5b0962079f73_r.jpg?source=1940ef5c)

**GitHub 卡片**
-------------

> Github 有很多动态生成的官方统计信息，利用这些统计信息我们可以更清晰地展现个人 Github 中的提交、分类、热门等信息。

卡片链接:`https://github-readme-streak-stats.herokuapp.com?user=dongyuanwai&theme=radical`

把下面的这段代码复制到你的 README.md 文档中, 将`username=`自己的 gitHub 名字, 就可以得到卡片样式

```
<div align="center">  
  <img  src="https://github-readme-streak-stats.herokuapp.com?user=dongyuanwai&theme=onedark&date_format=M%20j%5B%2C%20Y%5D" />
</div>

```

![](https://pic1.zhimg.com/v2-f290311af1d47109b60a5cb372ded68d_r.jpg?source=1940ef5c)

### **统计卡片**

stats 卡片链接：`https://github-readme-stats.vercel.app/api?username=dongyuanwai&theme=dark&show_icons=true`

把下面的这段代码复制到你的 README.md 文档中, 将`username=`自己的 gitHub 名字, 就可以得到卡片样式

```
![Dong Yuanwai's GitHub stats](https://github-readme-stats.vercel.app/api?username=dongyuanwai&show_icons=true)

```

![](https://picd.zhimg.com/v2-0beb230f62ddc0ef922fbf189f4f0804_r.jpg?source=1940ef5c)

gitHub-readme 文档可以不仅可以使用 mardown 语法，还支持 html 语法。所以你可以进行插入图片、设置位置等操作

**[数据牌](https://www.zhihu.com/search?q=%E6%95%B0%E6%8D%AE%E7%89%8C&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A2495155944%7D) - 徽章**
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

在浏览 GitHub 项目的时候，经常可以发现很多项目使用数据牌进行展示项目的数据，不仅实用，还有美化的作用

![](https://pic1.zhimg.com/v2-a760f4e117a407efd135f3a088868f96_r.jpg?source=1940ef5c)

静态徽章链接:`https://img.shields.io/badge/`

把下面的这段代码复制到你的 README.md 文档中, 将`左面文案`-`右边文案`-`右边背景色`, 就可以得到静态徽章样式

```
<img src="https://img.shields.io/badge/gitHub-%E8%AE%A9%E8%87%AA%E6%88%91%E4%BB%8B%E7%BB%8D%E5%8F%98%E5%BE%97%E6%9B%B4%E5%A5%BD-brightgreen" />

```

![](https://picd.zhimg.com/50/v2-bd723cfccd56138a8afdbcb1fd725791_720w.jpg?source=1940ef5c)![](https://picx.zhimg.com/v2-573bf00354b7fb8c74dc4bd98e3685c0_r.jpg?source=1940ef5c)

最后
--

![](https://picd.zhimg.com/v2-807e76c12b670aab4537c5e89164ef46_r.jpg?source=1940ef5c)

作为一个不停折腾的小 boy，后续还会整理更多有趣好玩的内容放到这里

[](https://link.zhihu.com/?target=https%3A//github.com/dongyuanwai/readme-become-better)

里面不仅有让 readme 变得更好的内容还有许多有趣的图片

![](https://pic1.zhimg.com/v2-fe36ddc508e46ac77dd1074484f12bd7_l.jpg?source=1940ef5c)程序员客栈​

GitHub 项目堪称教科书的 README，那一定要推荐 Standard Readme。

看名字你应该就知道这是什么了，就是标准 README 应该写哪些内容，应该怎样排版等等。

先放上链接：

[](https://link.zhihu.com/?target=https%3A//github.com/RichardLitt/standard-readme)

这个 README 标准是由 [RichardLitt](https://link.zhihu.com/?target=https%3A//github.com/RichardLitt) 发起，十多名开发者共同贡献完成的，在 GitHub 上有 1230+ Star。

![](https://picd.zhimg.com/50/v2-b35b000c9a140a665b477b26df2338e1_720w.jpg?source=1940ef5c)

你的 README 文件通常是你开源项目的第一个入口点。你应该通过 README 明确地告诉大家，为什么他们应该使用你的项目，他们如何安装它，以及他们如何使用它。

因此我相信很多人急需一份标准化的 README 编写方式，帮助你更轻松地创建和维护 REAMDME。所以 Standard Readme 这个项目就诞生了。

**一个标准的 README 应该包含哪些内容呢：**

![](https://pic1.zhimg.com/50/v2-aa37b52da89a9fd88244e12a866676c1_720w.jpg?source=1940ef5c)

*   项目背景
*   安装
*   使用
*   Badge
*   相关项目（可选）
*   主要项目负责人
*   参与贡献方式
*   开源协议

项目背景很简单，就是你为什么做这个项目，动机和背景是什么。

安装和使用也很简单，清晰明了即可，例如：

![](https://pic1.zhimg.com/50/v2-0820ed1d172034062a8aa9006054c0bf_720w.jpg?source=1940ef5c)

Badge 是一个很好玩的东西，当然是可选的，非必须。如下图：

![](https://picd.zhimg.com/50/v2-0f23702fc7be6aff3dad658fdf2d9f8d_720w.jpg?source=1940ef5c)

相关项目就是还有哪些与你做的类似的项目，如果你感兴趣可以列出来，例如：

![](https://pic1.zhimg.com/50/v2-1354e29e33d2dbbf9d162b9c440a413a_720w.jpg?source=1940ef5c)

项目主要负责人可以通过很多方式展现出来，直接艾特标注是最简单的方式：

![](https://pic1.zhimg.com/50/v2-365beeaa8bfe26041e55e1546cc48cf5_720w.jpg?source=1940ef5c)

参与贡献方式就是写清楚大家可以怎样参与这个项目的贡献，可简单，可繁琐，例如：

![](https://pic1.zhimg.com/50/v2-c5418aa751b681bafddf199b9e8efc0d_720w.jpg?source=1940ef5c)

License 就是你这个项目的开源协议，具体可以阅读协议介绍去选择一款适合你的：

![](https://pica.zhimg.com/50/v2-967b096e3293a19aecda9a7154f04a6f_720w.jpg?source=1940ef5c)

以上就是一个 GitHub 项目的 README 应该具备的内容，这个回答对你有帮助的话就点个赞吧～

![](https://picd.zhimg.com/ceb4931b6d9fe26a7ae1251b32e41cb4_l.jpg?source=1940ef5c)phodal​​

泻药。

先引用我在 《[GitHub 漫游指南 - github-roam](https://link.zhihu.com/?target=http%3A//github.phodal.com/%23readme)》相关部分的文章。在一个开源项目里，README 是最重要的内容。它快速地介绍了这个项目，并决定了它能不能吸引用户：

*   **这个项目做什么？**
*   **它解决了什么问题**
*   **它有什么特性** — **hello, world 示例**

这个项目做什么——一句话文案
--------------

GitHub 的 Description 是我们在 Hacking News、GitHub Trneding 等等，第一时间看到的介绍。也是我们能快速介绍给别人的东西，如下图所示：

![](https://picd.zhimg.com/50/v2-ceb36206e3091d822e957cd38c16c260_720w.jpg?source=1940ef5c)

这一句话，必须简单明了也介绍，它是干什么的。

如 Angular 的一句话方案是：One framework. Mobile & desktop.

而 React 是：A declarative, efficient, and flexible JavaScript library for building user interfaces.

Vue 则是：A progressive, incrementally-adoptable JavaScript framework for building UI on the web.

它解决了什么问题
--------

上面的一句话描述，它不能很好地说明，它能解决什么问题。

如下是今天在 GitHub Trending 上榜的 RPC 项目的简介：

> Most machines on internet communicate with each other via TCP/IP. However TCP/IP only guarantees reliable data transmissions, we need to abstract more to build services:

![](https://pic1.zhimg.com/50/v2-357cfbaaa630c852b51e5ac02ee87603_720w.jpg?source=1940ef5c)

以上便是这个项目能解决的问题，不过这个项目能解决的问题倒是比较长，哈哈哈。

它有什么特性
------

当我们有 A、B、C 几个不同的框架的时候，作为一个开发人员，就需要对比他们的特性，。如下是 Go 语言实现的 MQTT 示例：

![](https://pic1.zhimg.com/50/v2-7bb4cee37ccbdc0f92b681477530c147_720w.jpg?source=1940ef5c)

这个项目只支持的 Qos 级别为 0。如果我们需要的级别是 1，那么就不能用这个项目了。

又比如 lodash 项目：

> Lodash makes JavaScript easier by taking the hassle out of working with arrays, numbers, objects, strings, etc. Lodash’s modular methods are great for:

*   Iterating arrays, objects, & strings
*   Manipulating & testing values
*   Creating composite functions

你会怎么写？脸皮够厚的话，可以直接写一下，与其它项目的对比，blabla：

![](https://picd.zhimg.com/50/v2-07a764ebc07fa51fcf3c2a418489ebec_720w.jpg?source=1940ef5c)

当然了，这种事不能太过，要不然会招来一堆黑。

安装及 hello, world 示例
-------------------

在我们看完了上面的介绍之后，紧接着接一个 hello, world 的示例。在运行 hello, world 之前，我们可能需要一些额外的安装工作，如：

```
npm install koa

```

如 Koa 的示例：

```
const Koa = require('koa');
const app = new Koa();

// response
app.use(ctx => {
  ctx.body = 'Hello Koa';
});

app.listen(3000);

```

作为一个程序员，你应该懂得它的重要性。

好在这里的安装工作只有两步，而不是：

![](https://picx.zhimg.com/50/v2-2afa2ebfbc62656075b5dcb4287acd11_720w.jpg?source=1940ef5c)

对于那些需要复杂的安装过程的软件，应该简化安装过程，如提供 Docker 镜像，或者直接提供一个可运行的 Demo 环境。以免用户在看完 README 之后，直接放弃了使用该库。

基于上述的标准，我觉得我用过的这几个不错

[koajs/koa](https://link.zhihu.com/?target=https%3A//github.com/koajs/koa)

[encode/django-rest-framework](https://link.zhihu.com/?target=https%3A//github.com/encode/django-rest-framework)

不过，现今的趋势是引流到自己的官网上，这样可以获得流量、品牌效应和广告费等等。如 Angular、React、Vue 就这样成了 README 不好的例子