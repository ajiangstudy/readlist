> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/497671233)

> 如今，如果你仅仅为了更好的分享或者记录东西，想做一个博客；静态博客几乎是最好的选择。不需要太多的技术含量，网上有大把的教程，不需要花钱买服务器，甚至不需要花钱买域名。 这篇文章是在使用 hugo 将博客搭…

如今，如果你仅仅为了更好的分享或者记录东西，想做一个博客；静态博客几乎是最好的选择。不需要太多的技术含量，网上有大把的教程，不需要花钱买服务器，甚至不需要花钱买域名。

这篇文章是在使用 hugo 将博客搭建起来的基础上，摸索出来的一套写作流程。可有最大程度上简化除了写作之外的流程。

️前提
---

这篇文章的前提是你已经通过 hugo 和 github 搭建起来一个可以访问的 Github Pages 主页。如果尚未完成这个步骤，建议通过其他教程先做到这一步。

当前痛点
----

在当前的流程中，假如你需要新建一篇文章并发布，大体流程如下：

1.  打开命令行工具，切换到博客目录下，执行 `hugo new posts/newarticle.md` 创建一个新页面
2.  构思编写文章，如果中途需要贴图片，需要先将图片拷贝到指定静态资源目录下或者上传到图床并复制外链到剪贴板，然后在文章中通过图片引入语法添加图片。
3.  文章写完之后，再次打开命令行工具，切换到博客目录下，执行 `hugo -D` 编译静态网站文件。
4.  通过 git 命令行或者图形话工具，将更新上传至 Github 仓库中。完成！

以上便是发布一篇文章的基础工作，其中最麻烦便是图片资源的管理以及来回切换工具操作。

☝️如何解决
------

### 1. 自动编译

首要解决的问题是如何才能不需要每次手动编译之后再上传。这也是最好解决的部分。我们可以搭配 Github Actions 使仓库在更新的时候自动编译部署。

> Github Actions 是 Github 提供的一套持续集成服务。

操作流程：

1.  在仓库的根目录新建 .github/workfolws 目录
2.  在 .gitub/workflows 目录中新建流程配置文件 `main.yml`
3.  在 `main.yml` 中配置每当监听到仓库提交更新，就触发编译，并将编译后的静态网页部署在 `gh-pages` 分支。

文件目录如下：

![](https://pic1.zhimg.com/v2-558340bc32b247cea60f29a4e294b42c_r.jpg)

配置内容如下：

```
name: blog deploy pipline
on:
    push:
    tags:
        - '*'
    branches: [ main ]
 
env:
    REGISTRY: ghcr.io
    IMAGE_NAME: ${{github.repository}}

jobs:
    build:
        runs-on: ubuntu-latest
        concurrency:
            group: ${{github.workflow}} - ${{github.ref}}
        steps:
            - name: checkout
              uses: actions/checkout@v2
              with:
                submodules: true
                fetch-depth: 0
            - name: setup hugo
              uses: peaceiris/actions-hugo@v2
              with:
                hugo-version: '0.92.0'
                extended: true
            - name: build
            run: hugo --minify
            
            - name: deploy
            uses: peaceiris/actions-gh-pages@v3
            if: ${{github.ref == 'refs/heads/main'}}
            with:
                github_token: ${{secrets.GITHUB_TOKEN}}
                publish_dir: ./public

```

通过以上配置，每当 `push` 新内容的时候，就会在 github 仓库触发这个名叫 `blog deploy pipline` 的 `workflow` ，`workflow` 会将执行编译操作，并将编译之后的文件部署在 `gh-pages` 这个分支。

执行效果如下：

![](https://pic2.zhimg.com/v2-9c05e1b599fc7c7ca37f577b9019a215_r.jpg)

### 2. 选择合适的编辑器

写作最重要的便是找到一款功能垂直，颜值过关的编辑器。在尝试了几乎所有 `markdown` 编辑器之后，终于找到一款能够满足几乎说有需求的工具。

解决了手动编译的问题之后，其余的问题都可以通过 Obsidian 编辑器解决，

> Obsidian 是一款非常流行的双链编辑器，其强大的插件功能，使得这个编辑器仿佛一把瑞士军刀，能够满足诸多场景下的使用需求。

[⬇️ Obsidian 下载地址](https://link.zhihu.com/?target=https%3A//obsidian.md/)

需要注意的是，由于 Obsidian 对 markdown 语法进行了很多丰富，因此在使用 Obsidian 进行创作的时候，一些特殊语法是不能使用的，否则 hugo 的 markdown 解释器无法解析相应的语法。

### 2.1 创建文章

通常情况下，我们需要执行 hugo 提供的创建命令新建文章，这样就需要切换到命令行在切换回编辑器。

Obsidian 有一款插件叫 QuickAdd，这个插件的 Macro 模式可以快速执行 js 脚本，我们的办法就是通过 js 脚本将创建命令进行封装，通过调用 QuickAdd 命令，快速创建新文章。

1.  插件安装

打开设置中心，选择第三方插件中心，点击浏览按钮打开插件中心。

![](https://pic2.zhimg.com/v2-fca855896318f34dd910fd755d728641_r.jpg)

在搜索框中输入 QuickAdd 搜索插件，在 QuickAdd 插件中点击安装进行安装。

![](https://pic1.zhimg.com/v2-4b24604cdf9d6e0311e740c753e212cc_r.jpg)

1.  插件配置

在博客的根目录中新建 obs_sctipts 目录用于存放 QuickAdd 脚本文件，在目录中新建 NewBlog.js 脚本文件，脚本内容如下：

```
const util = require('util');
const child_process = require('child_process');
const exec = util.promisify(child_process.exec);

  
function getCreateTimeAsFileName() {
     var d = new Date();
     var year = d.getFullYear();
     var month = d.getMonth()+1;
     var day = d.getDate();
     var hour = d.getHours();
     var minute = d.getMinutes();
     var second = d.getSeconds();
     var time = year+"m"+month+"d"+day+"h"+hour+"m"+minute+"s"+second;
     return time;
}

  

// execute command function

async function executeCommand() {
     const fileName = getCreateTimeAsFileName()+".md";
     const { stdout, stderr } = await exec('hugo new posts/' +fileName,{cwd: app.fileManager.vault.adapter.basePath});
     console.log('stdout:', stdout);
     console.log('stderr:', stderr);
     if (stdout) {
         new Notice("New Blog Created["+fileName+"]")
     }else{
         new Notice("New Blog Create Faild. "+stderr)
     }
}

  

module.exports = async function(context, req) {
    await executeCommand();
}

```

在第三方插件中找到 QuickAdd 插件，点击配置按钮进行配置。

![](https://pic1.zhimg.com/v2-d3c1012fdacaf9ba6e417f18adb2addc_r.jpg)

点击 Manage Macros 创建宏

![](https://pic1.zhimg.com/v2-19d0e1ed9bcae63b3178ddf94f3dbe04_r.jpg)

输入名字点击 Add Macro

![](https://pic4.zhimg.com/v2-a264beeec725e1b236234e83445615ef_r.jpg)

在新建的宏下方点击 Configure 对宏进行配置

![](https://pic2.zhimg.com/v2-40d9f2cf23c752cc26a47701d8716ee9_r.jpg)

在 User Scripts 后的输入框中选择创建的 js 脚本 NewBlog，点击 Add 添加

![](https://pic2.zhimg.com/v2-03fc6bc37619c0488a9d035309ac5f2d_r.jpg)

到这里，创建文章的命令就配置完成了

1.  使用方法

打开 Obsidian 编辑器，通过 `ctrl+p` 快捷键换出命令输入框

![](https://pic2.zhimg.com/v2-4ec0a47602b03286d7154649477ab09d_r.jpg)

在命令输入框中输入 QuickAdd 点击回车

![](https://pic2.zhimg.com/v2-e057ad414d0fe65d146d249d80003fa1_r.jpg)

弹出创建博客的命令之后再次回车

![](https://pic4.zhimg.com/v2-0ff8891e13950c897a90966c5d010343_r.jpg)

一篇文章就创建好了，在 content/posts 中可以找到对应的 md 文件

![](https://pic2.zhimg.com/v2-efefde4f51c5fbd7a6a0897ca2d1df6d_b.jpg)![](https://pic3.zhimg.com/v2-ce0f6d82754284b5dadeb024fb4b1ca6_r.jpg)

### 2.2 静态资源管理

解决了自动化创建文章这座大山之后，还有另外一座更大的叫静态资源管理大山需要克服。

静态资源管理一般分为两种办法：

1.  随仓库一起托管在 github，通过相对路径进行引用。
2.  单独托管在图床，通过外链引用

这里推荐使用办法 2，通过图床进行统一管理，能保证访问速度，方便迁移。

Obsidian 有一款插件叫 `Image auto upload plugin` ，可以结合 PicGo 将图片同步传到图床，并将外链插入文章中。不需要我们额外进行静态资源管理。将图片粘贴或者拖拽到需要插入图片的地方即可。

具体的操作办法如下：

1. 安装 PicGo 并配置相应的图床，PicGo 支持 SM.MS、腾讯云 COS、Github 图床、七牛图床、Imgur 图床、阿里云 OSS、又拍云图床等众多常用图床。

[⬇️ PigGo 下载地址](https://link.zhihu.com/?target=https%3A//github.com/Molunerfinn/PicGo/releases)

PicGo 的配置可以自行百度解决。

1.  安装 `Image auto upload plugin` 插件并开启，具体安装方式同参考上文中 QuickAdd 的安装。

完成以上两步操作之后，便可以在文章中通过粘贴或者拖拽的方式添加图片资源。

### 2.3 文章提交

通过以上步骤，基本上写作流程已经比较完美了。如果能够简化提交流程就更加完美了。

巧了，Obsidian 有一个 git 插件可以通过快捷命令的方式将修改内容提交到 github。这个插件的名字叫 `Obsidian Git`，具体的安装方式就不再介绍了。着重介绍一下操作方式。

1.  通过 `ctrl+p` 快捷键换出命令窗口
2.  输入 `git commit` 命令，将本地修改提交
3.  再次换出命令窗口并输入 `git push` 命令，将修改提交到远程 Github 仓库

稍等一会，等 Github Actions 执行完成之后，便可以在你的博客中看到最新内容了。

3. 总结
-----

整体流程，通过结合 Github Action 以及 Obsidian 的众多优秀插件，实现了在 Obsidian 中不切换其他工具的情况下，完成文章的创建、编写、提交、推送。让写博客真正的以写为主。

4. Obsidian 其他插件推荐
------------------

1.  Obsidian Pangu，一个中英文混编格式化插件，可以在英文与中文之间自动添加空格
2.  Emoji Tookbar，一个 Emoji 插件，提供 Emoji 选择面板，可以快速添加表情