> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.jianshu.com](https://www.jianshu.com/p/ba63900433c7)

> 关键字 Obsidian教程 模板 插件 2021年4月7日声明 插件Templater在2021年4月6日进行了更新，其内部模板（后称内部模板）发生了极大的变化，我会在不影...

关键字
---

*   Obsidian 教程
*   模板
*   插件

2021 年 4 月 7 日声明
----------------

插件 Templater 在 2021 年 4 月 6 日进行了更新，其`内部模板`（后称`内部模板`）发生了极大的变化，我会在不影响工作的前提下尽早经行更新。读者如不耐其烦，可先行浏览 [Templater 官方文档](https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2FSilentVoid13%2FTemplater)。此次更新对于本文中关于 Obsidian 核心插件`模板`内容没有任何影响。

约定和声明
-----

本文中会提及三种形式的 Obsidian **模板**：

1.  由 Obsidian 作者自行创建的核心插件 Template，在翻译为中文后被称为 “模板”。该插件提供了一组变量参数，可在被调用时自动替换文件名以及日期时间信息。
2.  Obsidian 第三方插件 Templater 提供了更为丰富的变量，插件作者也将其称之为 “模板”，在日常实践中单独使用 Templater 即可。安装 Templater 当然可以利用 Obsidian 客户端，同归之径是从 [GitHub 的 Templater 代码仓库](https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2FSilentVoid13%2FTemplater%2Freleases)下载。
3.  使用上述两种插件后，可在文档中添加大量变量以备后续之用。这些具备 “框架” 性质的文档，也应被称作“模板”。

凡此种种必须加以区分，否则思绪错综难于理解。因此，对各种使用情景辨析如下：

1.  Obsidian 核心插件 Template 在简体中文 UI 中被定名为 “模板”。为维持一致性，文中所有提及该插件时都会使用 “模板”。
2.  **模板**之所以强大高效，在于内置 “变量” 在被调用时可被替换为对应的信息，以不变应万变。例如，核心插件 “模板” 所含变量`{{date}}`会被替换为当天日期。后续为核心插件”模板”内置的 “变量” 均称为”模板变量“。
3.  第三方插件 Templater 是核心插件”模板 “的极大超集。对应于” 变量 “也加以区分：其一为 Templater 系统所内置，被称为” 内部变量 “。其二为使用者自定予以定制，可称为” 定制变量“。
4.  对于使用了众多 “变量” 的文本文件，我做了变通处理，全文做 “模板样章” 或“样章”使用。

概述和背景
-----

我们大约都听说过这样一句话：

> 复杂的事情简单做，简单的事情重复做，重复的事情用心做。

确实，无论是专家、行家还是赢家，唯有做事才能成就自己和周围的一切。而本文要阐述的就是如何在 Obsidian 中使用**模板**（Template）“套壳” 撰写文章。在日常实践中，使用第三方插件`Templater`即可。但假如使用者更加注重安全和稳定，亦或无法下载安装第三方插件，Obsidian 核心插件`模板`也有其实用之处。

易学易用的核心插件 “模板”
--------------

Obsidian 中的绝大多数功能都是以插件的形式提供的，有些插件甚至为 Obsidian 的开发者自行研发，这些插件提供了很多非常基础和实用的功能。正式透过这些被称为**核心插件**（Core plugins）的功能，在使用 Obsidian 的过程中渗透出卡片式写作（Zettelkästen）的文化和哲学。本文所要着重阐述的模板就是其中之一。只需少许学习外加一点巧思，就能非常便利地为描摹出文章的大致框架。

### “模板” 基础概念

Obsidian 核心插件`模板`，相较于第三方插件`Templater`更简单且易于掌握。在 Obsidian 中，无论何种类型的插件，在使用之前都需予以手动开启。操作路径依次为：

> `设置` 按键→ `核心插件`页面 → 开启`模板`选项

开启 Obsidian 核心插件模板之后，还需要配置适当才能使用。其操作路径为：

> `设置`按键 → `插件选项`选区 → `模板`页面

![](http://upload-images.jianshu.io/upload_images/1612158-d9f0376d4bb4a7f3.png) 配置核心插件 “模板”

**重点**在于：

1.  模板样章须集中存放，如此便于配置时予以指定。依我使用习惯，所有的样章都贮存于`010-Templates`目录。其中，既有日记、文章，也有 todo-list 其他形式的样章。需要注意的是，**文档库彼此独立**，相互之间都可单独安装、设置不同的插件和主题。因此，样章文件夹必须与文档库一一对应，**样章文件夹也必须置于文档库统辖之内**。  
    ![](http://upload-images.jianshu.io/upload_images/1612158-927c5b05b527484a.png) 我的 “模板文件夹” 中保存了多种不同目的和作用的样章文件
2.  我们可以指定默认的**日期**和**时间**显示格式。一旦设定妥当，今后使用`{{date}}`日期变量和`{{time}}`时间变量表征当前日期和时间。具体说明配置细节，请参阅下一条目。
3.  内部变量就是用来折腾的，假如不习惯样例中的格式，可以学习 [Moment.js 中相关日期和时间格式的文档说明](https://links.jianshu.com/go?to=https%3A%2F%2Fmomentjs.com%2Fdocs%2F%23%2Fdisplaying%2Fformat%2F)后自行调整 [[1]](#fn1)，适用性囊括核心插件`模板`和第三方插件`Templater`，包括了所有关于日期和时间格式化字符串的描述。
4.  如果怕 “污染” 模板环境，可在调用内部变量时饰以参数，用于调整显示效果。例如：`{{date:MMM. Do. YYYY}}`表征的是形如 **Mar. 10th. 2021** 的日期格式。其中：
    *   `{{date}}`是日期变量，代表当天日期。而 `MMM. Do. YYYY`是其参数，被才成为格式化字符串，用于说明以何种方式进行显示。需要**特别注意**的是，`:`负责在内部变量与参数施以间隔，不可或缺。
    *   `{{date:MMM}}`代表三位字母的英文月份简写（即 **Mar**）。
    *   `{{date:Do}}`表示英文序数词类型的日期（即 **10th**）
    *   `{{date:YYYY}}`为四位数字年份（即 **2021**）。
    *   穿插于格式化字符串之间的符号`.`和（**空格**字符）仅用于占位显示。占位字符当然绝非仅限此两种，除特定意义字符外，绝大多数中英文信息都可胜任。
    *   如此格式化字符串使用起来极为繁复，如不纠结细节，可代之以`{{date:ll}}`。其显示结果形如 **Mar 10, 2021**。
5.  除了日期变量`{{date}}`和时间变量`{{time}}`之外，变量 `{{title}}`用于表示当前文件（标题）的名称。

**谜题时间**：  
读者在学习过日期和时间变量，以及格式化字符串的相关知识后，是否能设计形如 **2021 年 3 月 25 日 星期 4** 的日期字符串？

### 如何 “套壳” 样章？

有了样章，还需要套壳才能使用。但要如何套用？还需要详细阐述。

假设我已在`010-Templates`（核心插件**模板**中设定此目录为 “模板文件夹”）中创建了样章`new-template`。其中内容如下：

```
# {{title}}

{{date}}是个**好日子**，特别是{{time}}更是特别！


```

我在`020-Dailies`[[2]](#fn2) 目录中创建文件`我今天的故事`。此时，我只需按下快捷热键`Ctrl` + `P`开启`命令面板`。为了加快搜寻速度，不妨键入 “模板” 二字，`插入模板`命令随即脱颖而出。键入`Enter`加以确认。  

![](http://upload-images.jianshu.io/upload_images/1612158-1985568048574698.png) 插入模板

用户样章众多，Obsidian 不知所求。在键入 “new” 后，筛选出了`new-template`。使用鼠标或再次键入`Enter`确认。  

![](http://upload-images.jianshu.io/upload_images/1612158-267443a31a968435.png) 选择套壳 new-template

于是，文档`我今天的故事`从空无一物变成了下面这般模样：  

![](http://upload-images.jianshu.io/upload_images/1612158-6a5105a867ca5871.png) 套壳样章 new-template 的效果

当然，实际使用时样章不可能如此随意，但陷于核心插件`模板`能力有限，复杂和实用的演示案例留待下节细数。

远为强大的第三方插件 Templater
--------------------

本文 “约定和声明” 时既已强调，Templater 高能强大之处在于众多不同类型的“内部变量”，以及可予订制的“定制变量”。如此搭配，既辖驭了众多而丰富的功能，同时开放接口外扩了灵活性，可以被运用于更多的使用场景之中。

因缘于此，稍作尝试`Templater`，核心插件`模板`就被我永久关闭。关闭核心插件`模板`的操作路径为：

> `设置`按键 → `核心插件`页面 → 关闭`模板`选项

### 安装并配置 Templater

安装第三方插件 Templater 的方法有两种：

*   通过 Obsidian 客户端安装，必备条件是需要拥有访问国际化网络的能力。
*   通过 [Templater 在 Github 的代码仓库](https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2FSilentVoid13%2FTemplater%2Freleases)下载后，解压缩至文档库下`.obsidian\plugins\`目录之中。不幸的是，近来 GitHub 断断续续也是访问异常。  
    ![](http://upload-images.jianshu.io/upload_images/1612158-799200aae3d66a01.png) 除了利用 Obsidian 客户端进行安装，也可从 Templater 在 GitHub 代码仓库下载后安装

![](http://upload-images.jianshu.io/upload_images/1612158-a186b6e2f4bcfa3a.png) 除了在客户端中直接安装，也可将下载插件并解压至 Obsidian 中的插件目录

开启 Templater 控制权限，操作路径为：

> `设置`按键 → `第三方插件`页面 → 开启`Templater`

之后，通过以下操作路径配置 Templater：

> `设置`按键 → `插件选项`选区 → `Templater`页面

![](http://upload-images.jianshu.io/upload_images/1612158-e98e7e62789d0ccc.png) 配置第三方插件 Templater

高效起见，快捷热键也需加以留意：

> `设置`按键 → `快捷键`页面 → 搜索 **Templater**

之后，会有如下提示选项可做配置：

![](http://upload-images.jianshu.io/upload_images/1612158-35503c5bf5a6e6b2.png) 使用快捷热键是提升效率的有效途径

**本节小结**：

1.  安装 Templater 需要依据网络条件变通解决。
2.  如果能够使用 Templater，则完全可以弃用核心插件 “模板”。
3.  配置时类似于 “模板”，必须指定众多样章的存储目录。
4.  配置选项中的`Locale`（地区）选项非常重要，会直接影响日期、时间的显示效果。使用 “Chinese(China)” 还是“English”，需要读者自行权衡斟酌。  
    例如：对应于日期变量`Thu, Mar 25, 2021 6:06 PM`，“Chinese(China)” 套壳样章后会替换信息形如 **2021 年 3 月 24 日星期三 17:46**，而 “English” 则为 **Wed, Mar 24, 2021 5:46 PM**。
5.  快捷热键可提高使用效率，建议读者熟练掌握。
6.  定制变量具体见后续小节说明。

### Templater 中的内置变量

比之核心插件模板，Templater 最为直观的印象，就是作者预先定义了大量直接可用的内置变量。这些内置变量灵活可、适用性强，稍加学习即可应用于绝大多数应用场景。

阅读文档通常是学习专业知识的终南捷径，插件作者笔耕不辍在 [GitHub 提供了内部变量的完整说明](https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2FSilentVoid13%2FTemplater%23internal-templates)。我自知浅薄，囫囵翻译之余略加注释，也就冗列于此：

<table><thead><tr><th>内部变量</th><th>参数</th><th>功能描述</th><th>代码示例</th><th>显示效果</th></tr></thead><tbody><tr><td><code>{{tp_title}}</code></td><td>无</td><td>取得当前文件的名称</td><td><code>{{tp_title}}</code></td><td><code>一文掌握Obsidian模板</code></td></tr><tr><td><code>{{tp_folder}}</code></td><td>- <code>vault_path</code>: 取得文本库到当前文件夹的相对路径。取值范围<code>true</code>或<code>false</code>，默认为<code>false</code>。</td><td>获取当前目录的名称。</td><td>1. <code>{{tp_folder}}</code><br>2. <code>{{tp_folder:vault_path=true}}</code></td><td>1. <code>Obisdian教程</code><br>2. <code>写作/技术类/Obsidian教程</code></td></tr><tr><td><code>{{tp_include}}</code></td><td>- <code>f</code>: 此为必填项。须指定从文档库开始到某一具体文件的相对路径，将该文件全部内容填充到当前文档中书写有<code>{{tp_include:f="location"}}</code>的位置。</td><td>将指定文件中全部内容的填入当前文档。指定文件可为另一样章，其中包含的变量也将解析替换（替换深度<code>10</code>）。</td><td><code>{{tp_include:f="location"}}</code></td><td></td></tr><tr><td><code>{{tp_date}}</code></td><td>- <code>f</code>: 指定日期格式化字符串，请参考 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmomentjs.com%2Fdocs%2F%23%2Fdisplaying%2Fformat%2F" target="_blank">Moment.js 中关于格式化字符串的相关文档</a> (缺省格式为: <code>YYYY-MM-DD</code>)。<br>- <code>offset</code>: 设置偏移天数，例如设定为<code>-7</code>时可获得上周日期 (默认值为<code>0</code>)。</td><td>取得今日 + 偏移天数的日期。</td><td><code>{{tp_date:f="ll", offset=7}}</code></td><td><code>Apr 1, 2021</code></td></tr><tr><td><code>{{tp_yesterday}}</code></td><td>- <code>f</code>: 指定日期格式化字符串，请参考 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmomentjs.com%2Fdocs%2F%23%2Fdisplaying%2Fformat%2F" target="_blank">Moment.js 中关于格式化字符串的相关文档</a> (缺省格式为: <code>YYYY-MM-DD</code>)。</td><td>取得昨天的日期。</td><td><code>{{tp_yesterday}}</code></td><td><code>2021-03-24</code></td></tr><tr><td><code>{{tp_tomorrow}}</code></td><td>- <code>f</code>: 指定日期格式化字符串，请参考 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmomentjs.com%2Fdocs%2F%23%2Fdisplaying%2Fformat%2F" target="_blank">Moment.js 中关于格式化字符串的相关文档</a> (缺省格式为: <code>YYYY-MM-DD</code>)。</td><td>取得明天的日期。</td><td><code>{{tp_tomorrow}}</code></td><td><code>2021-03-26</code></td></tr><tr><td><code>{{tp_time}}</code></td><td>- <code>f</code>: 指定时间格式化字符串，请参考 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmomentjs.com%2Fdocs%2F%23%2Fdisplaying%2Fformat%2F" target="_blank">Moment.js 中关于格式化字符串的相关文档</a> (缺省格式为: <code>HH:mm</code>)。</td><td>取得当前时间。</td><td>1. <code>{{tp_time}}</code><br>2. <code>{{tp_time:f="H:m:s"}}</code></td><td>1. <code>08:36</code><br>2. <code>8:36:9</code></td></tr><tr><td><code>{{tp_creation_date}}</code></td><td>- <code>f</code>: 指定日期格式化字符串，请参考 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmomentjs.com%2Fdocs%2F%23%2Fdisplaying%2Fformat%2F" target="_blank">Moment.js 中关于格式化字符串的相关文档</a> (缺省格式为: <code>YYYY-MM-DD HH:mm</code>)。</td><td>获取当前文档创建时的日期。</td><td><code>{{tp_creation_date}}</code></td><td><code>2021-03-21 13:03</code></td></tr><tr><td><code>{{tp_last_modif_date}}</code></td><td>- <code>f</code>: 指定日期格式化字符串，请参考 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmomentjs.com%2Fdocs%2F%23%2Fdisplaying%2Fformat%2F" target="_blank">Moment.js 中关于格式化字符串的相关文档</a> (缺省格式为: <code>YYYY-MM-DD HH:mm</code>)。</td><td>获取当前文档最后修改的日期。</td><td><code>{{tp_last_modif_date}}</code></td><td><code>2021-03-25 08:36</code></td></tr><tr><td><code>{{tp_title_date}}</code></td><td>- <code>title_f</code>: 指明适用于文档名称中的日期字符串格式。请参考 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmomentjs.com%2Fdocs%2F%23%2Fdisplaying%2Fformat%2F" target="_blank">Moment.js 中关于格式化字符串的相关文档</a> (默认格式为: <code>YYYY-MM-DD</code>)。此处设置应与核心插件 “日记” 中指定日期格式化字符串相同。<br>- <code>f</code>: 指定日期格式化字符串，请参考 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmomentjs.com%2Fdocs%2F%23%2Fdisplaying%2Fformat%2F" target="_blank">Moment.js 中关于格式化字符串的相关文档</a> (缺省格式为: <code>YYYY-MM-DD</code>)。<br>- <code>offset</code>: 设置偏移天数，例如设定为<code>-7</code>时可获得上周日期 (默认值为<code>0</code>)。</td><td>多用于 “日记”。可获取文件名中包含的日期 + 偏移天数。</td><td><code>{{tp_title_date:title_f="YYYY-MM-DD_dddd", f="YYYY-MM-DD"}}</code></td><td><code>2021-03-26</code></td></tr><tr><td><code>{{tp_title_yesterday}}</code></td><td>- <code>title_f</code>: 指明适用于文档名称中的日期字符串格式。请参考 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmomentjs.com%2Fdocs%2F%23%2Fdisplaying%2Fformat%2F" target="_blank">Moment.js 中关于格式化字符串的相关文档</a> (默认格式为: <code>YYYY-MM-DD</code>)。此处设置应与核心插件 “日记” 中指定日期格式化字符串相同。<br>- <code>f</code>: 指定日期格式化字符串，请参考 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmomentjs.com%2Fdocs%2F%23%2Fdisplaying%2Fformat%2F" target="_blank">Moment.js 中关于格式化字符串的相关文档</a> (缺省格式为: <code>YYYY-MM-DD</code>)。<br>- <code>offset</code>: 设置偏移天数，例如设定为<code>-7</code>时可获得上周日期 (默认值为<code>0</code>)。</td><td>多用于 “日记”。可获取文件名中包含的日期前一天 + 偏移天数。</td><td><code>{{tp_title_yesterday:title_f=="YYYY-MM-DD_dddd, f="YYYY-MM-DD"}}</code></td><td><code>2021-03-25</code></td></tr><tr><td><code>{{tp_title_tomorrow}}</code></td><td>- <code>title_f</code>: 指明适用于文档名称中的日期字符串格式。请参考 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmomentjs.com%2Fdocs%2F%23%2Fdisplaying%2Fformat%2F" target="_blank">Moment.js 中关于格式化字符串的相关文档</a> (默认格式为: <code>YYYY-MM-DD</code>)。此处设置应与核心插件 “日记” 中指定日期格式化字符串相同。<br>- <code>f</code>: 指定日期格式化字符串，请参考 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmomentjs.com%2Fdocs%2F%23%2Fdisplaying%2Fformat%2F" target="_blank">Moment.js 中关于格式化字符串的相关文档</a> (缺省格式为: <code>YYYY-MM-DD</code>)。<br>- <code>offset</code>: 设置偏移天数，例如设定为<code>-7</code>时可获得上周日期 (默认值为<code>0</code>)。</td><td>多用于 “日记”。可获取文件名中包含的日期后一天 + 偏移天数。</td><td><code>{{tp_title_tomorrow_title:title_f=="YYYY-MM-DD_dddd, f="YYYY-MM-DD"}}</code></td><td><code>2021-03-27</code></td></tr><tr><td><code>{{tp_daily_quote}}</code></td><td>无</td><td>利用 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fquotes.rest%2F" target="_blank">https://quotes.rest</a> 提供的 API 取得每日名言摘引。</td><td><code>{{tp_daily_quote}}</code></td><td></td></tr><tr><td><code>{{tp_random_picture}}</code></td><td>- <code>size</code>: 以如下方式设置图片尺寸 <code>&lt;宽&gt;x&lt;高&gt;</code>(默认值为: <code>1600x900</code>).<br>- <code>query</code>: 输入一个关键字用于限定选定图片的范围。如需使用多个关键字，彼此之间需要以英文半角<code>,</code>加以间隔。此时，还有另一注意事项：需使用英文双引号<code>"</code>用以在两端定界。(默认值为: 没有搜索关键字)</td><td>基于搜索关键字从 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Funsplash.com%2F" target="_blank">unsplash.com</a> 获取一张随机图片。</td><td><code>{{tp_random_picture:size="800x600", query="beijing"}}</code></td><td></td></tr><tr><td><code>{{tp_title_picture}}</code></td><td>- <code>size</code>: 以如下方式设置图片尺寸 <code>&lt;宽&gt;x&lt;高&gt;</code>(默认值为: <code>1600x900</code>).</td><td>基于笔记标题从 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Funsplash.com" target="_blank">unsplash.com</a> 获取一张随机图片。</td><td><code>{{tp_title_picture:size="800x600"}}</code></td><td></td></tr><tr><td><code>{{tp_cursor}}</code></td><td>无</td><td>将当前位置设定为套壳样章后游标的操作位置。</td><td><code>{{tp_cursor}}</code></td><td></td></tr></tbody></table>

**本节重点**：

1.  Templater 提供了更为丰富灵活的内部变量，形式上仍以`{{ }}`加以包络，但变量命名时以 **tp** 开头以避重复。
2.  比之核心插件模板，Templater 对于内部变量配置参数的方式变动较大。所幸日常使用仅需运用 Templater 一途即可。读者诸君聪明博学在我之上，稍加用心上表 “功能描述”、“代码示例” 和“输出效果”，定能触类旁通。  
    读者读后昏昏欲睡，只因我码字功利粗陋。于此之时，回顾 [Templater 文档](https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2FSilentVoid13%2FTemplater%23usage)有言：

> All internal template patterns are prefixed with the keyword `tp_` and are placed between double braces like so `{{tp_<name>}}`. This is to recognize them and to avoid conflicts with user defined templates.  
> Internal templates accept user arguments, they should be passed like so: `{{<template_name>:<argument_name1>=<argument_value1>,<argument_name2>=<argument_value2>}}`.  
> If your argument value contains a special character (`,` or `=`) you can add quotes around your argument value like so: `<argument_name>="<argument_value>"`. If you want to use a quote inside quotes, you can escape it like so: `\"`.

### Templater 中的定制变量

是否还记得配置 Templater 截图中的我私人订制的变量`{{北京天气}}`？  

![](http://upload-images.jianshu.io/upload_images/1612158-e98e7e62789d0ccc.png) 配置第三方插件 Templater

经过 Templater 解析处理，能实时将天气状况嵌入文档之中。其实，Templater 作者在[文档示例](https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2FSilentVoid13%2FTemplater%23user-templates)中也只小露一手，我只有嗟来之能。

Templater 定制变量与操作系统指令有关，使用者需要针对电脑操作系统自行订制开发，展现出更为宽阔的适用空间。可惜我学艺不精，仅只掌握了如何查询天气，共享与读者诸君。

<table><thead><tr><th>定制变量名称</th><th>功能描述</th><th>适用平台</th><th>对应代码</th><th>显示效果</th></tr></thead><tbody><tr><td><code>{{北京天气}}</code></td><td>利用工具<code>curl</code>从网站 <a href="https://links.jianshu.com/go?to=http%3A%2F%2Fwttr.in" target="_blank">wttr.in</a> 获取天气信息。低版本 Windows 如未内置<code>curl</code>，请用户自行下载并置于搜索路径之内。</td><td>Windows、Linux、Mac</td><td><code>curl "curl -H "Accept-Language: zh-CN" "wttr.in/Beijing?format=2""</code></td><td>☀️ 🌡️+21°C 🌬️↑19km/h</td></tr></tbody></table>

其中，代码信息对应为：

1.  `Beijing`是需查询天气的城市名称，仅适用于英文名称。
2.  `format=2`为天气的实现形式，可选范围 1~4，各自有所不同。
3.  `Accept-Language: zh-CN`，对应于显示语言和本地天气信息样式。

### Templater 套壳样章

我现在使用的文章写作样章命名为`paper-template`，形式如下：

```
---
author: your_name
created: {{tp_date:f="llll"}}
aliases: [{{tp_title}}]
description:
tags:

---

# {{tp_title}}



## 关键字



## 概述和背景




---
## 注释





```

其中：

*   YAML 区 metadata 大致描述了文档作者、创建时间和其他分类信息，便于日后检索。
*   一级标题、文档别名，与文档名称相同，一目了然。

需要创建文档时，调用 Templater 内置的快捷热键`Alt` + `E`，即可弹出菜单挑选需要应用的样章。其形式与核心插件 “模板” 相同：  

![](http://upload-images.jianshu.io/upload_images/1612158-d8a288d354b2951b.png) Templater 筛选样章的过程与核心插件模板相同

套壳样章后，会建立类似如下文档：

![](http://upload-images.jianshu.io/upload_images/1612158-6624e166d911e032.png) 套壳 Templater 的文章

**本节重点**：

1.  Templater 套壳样章的方法与核心插件 “模板” 相同，须将所有样章置于配置时指定的 “样章文件夹” 内。
2.  套壳时，可使用 Templater 默认的快捷热键`Alt` + `E`，在弹出的对话框内选用具体样章。
3.  在写作文档的过程中，也可适时填写 Templater 内置变量或定制变量。如需解析时，可使用默认快捷热键`Alt` + `R`自动完成。

注释
--

1.  **Obsidian 模板与 Moment.js**：毫无疑问，Obsidian 在设计模板功能时是使用到了 Moment.js 这个 “轮子”。所以，在修改默认日期和时间格式时，Obsidian 作者直接让用户参考 Moment.js 文档。而本文另一个重点介绍的第三方插件同样调用了 Moment.js 来格式化日期和时间字符串。当然，作为非专业人士的普通用户面对如此庞杂的信息能面心生怨尤，但事实上我们只需查询文档并做少量修改即可。 [↩](#fnref1)
    
2.  **套用样章的文件与所处目录无关**：套用样章的关键在于配置`模板`插件时，指定样章文件夹。至于新创建的文件处于何位置，其实与套用样章无关。换言之，只要文件处于文档库内，随时随地可以套用样章，甚至多次套用不同样章。极端示例是样章互为嵌套，此种情景绝少发生。同时，套用样章只是在文末续写，所以非常安全。  
    事实上，在我的文档库中`020-Dailies`目录对应的是另一款核心插件`日记`。将文档`我今天的故事`添加于此，只求截图便利，实属下策。当然，读者有何使用习惯纯属审美习惯，不能一概强求。关于笔记分类归档的知识，建议读者自行学习 MOC 和 PARA 技术。 [↩](#fnref2)