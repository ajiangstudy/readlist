> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [github.com](https://github.com/Reamd7/notion-zh_CN)

> notion 中文化. Contribute to Reamd7/notion-zh_CN development by creating an account on GitHub.

[](#官方中文条数已经到7063条啦韩文是7066官方中文已经在路上了)官方中文条数已经到 7063 条啦！！，韩文是 7066！！，官方中文已经在路上了
==============================================================================

[](#notion-zh_cn-是什么)notion-zh_CN 是什么？
======================================

notion-zh_CN 是对 notion 的汉化脚本。 2.0 版本支持网页端 (油猴脚本)+ 桌面端。 2.2.0 安卓版本 notion，与官方版共存。 2.3.0 cloudflare worker 代理，提供加速以及平台无关的汉化能力。

> 风险提示：使用 cloudflare worker 的同学，被官方检测出来并封号与我无关，希望自己看明白代码做了什么，以及为什么会被检测出来。 其他方式的，都是使用官方国际化方案进行国际化的，而且在本地进行操作不通过任何服务器——理论上除非故意钓鱼否则不会封你。 钓鱼：主动收集你是不是用了中文版国际化字段，而且，对比你并没有中文版权限。
> 
> 如果担心有问题，可以等待官方中文版，可以稍微学习网页开发，可以询问网页开发朋友，项目都是开源的。究竟做了什么操作，对 notion 应用本体有什么影响，没有理由的担心只能体现对别人的不信任。
> 
> 该项目仅用于学习，如有侵权 24h 内会马上删除。

[](#功能)功能
---------

1.  网页端 (油猴脚本) + 桌面端 ( win / mac ) 支持最新版本
    
    > 未来官方支持中文版也会跟进（如果官方做得好就可以功成身退了）
    
2.  支持 中文 / **拼音** 快捷键输入（2.1.0 支持）
    
    > 支持拼音快捷键是便于英文，中文同时输入的时候不用反复切换输入法来保证快捷键输入。
    
3.  2.2.0 支持安卓版本 notion 的汉化！
    
    > 在 apk 中注入 android.js 的代码，远程下载 runtime.js 注入汉化文本 2.3.1 长白屏时间，换全汉化
    
4.  2.3.0 提供 cloudflare worker 版本代理 notion.so 域名 这是一个**平台无关**（IOS 上的 safari 也能直接使用）的汉化方式，只要你自己部署 cloudflare worker，就可以使用。附带 cf 代理**加速**的能力。
    
    > 其实这里应该可以做域名映射到 notion.so 的访问的。(从而实现全平台汉化)
    

[](#为什么要做这个项目)为什么要做这个项目？
========================

1.  ~感谢社区汉化的 4189 条中文词条，可是官方关闭了中文版入口。原因能够理解，毕竟 notion 在发展，韩文版已经到 5563 条了，国际化远远跟不上官方软件发展的速度。而且最核心的，是只有韩文版有官方帮助文档的翻译。整个本地化的东西都没完善，也不能开放入口。~
    
2.  **官方中文条数已经到 7063 条啦！！，韩文是 7066！！，官方中文已经在路上了**
    
3.  国内市场还是有需求中文版本的使用的，~即便是临时，给国内用户一个方式以临时使用中文汉化语言环境。你英语好不好与我无关，我只是希望把缺失的词条用机器翻译的方式补充回来，即便是看得懂也想机翻。~不用机器翻译了，官方中文条目已经开始维护了。够用了够用了
    

[](#更新日志)更新日志：
==============

*   2.4.2 **翻译开始跟随着官方中文词条啦!!!!!**
*   2.4.1 支持 ios / macos user script
*   2.3.1 权衡后，安卓版本使用新的 runtime 注入方式，实现全部的（包括键盘都能够汉化的方式）但有首页白屏事件较长的问题。
*   2.3.0 支持使用 cloudflare worker 进行代理 notion.so 域名进行加速及国际化
*   2.2.0 支持 安卓版本 notion，与官方版共存 的汉化！
*   2.1.0：支持中文版快捷命令！支持拼音输入的时候显示快捷命令！ [![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAACbklEQVRoQ+2aMU4dMRCGZw6RC1CSSyQdLZJtKQ2REgoiRIpQkCYClCYpkgIESQFIpIlkW+IIcIC0gUNwiEFGz+hlmbG9b1nesvGW++zxfP7H4/H6IYzkwZFwQAUZmpJVkSeniFJKA8ASIi7MyfkrRPxjrT1JjZ8MLaXUDiJuzwngn2GJaNd7vyP5IoIYY94Q0fEQIKIPRGS8947zSQTRWh8CwLuBgZx479+2BTkHgBdDAgGAC+fcywoyIFWqInWN9BSONbTmFVp/AeA5o+rjKRJ2XwBYRsRXM4ZXgAg2LAPzOCDTJYQx5pSIVlrC3EI45y611osMTHuQUPUiYpiVooerg7TWRwDAlhSM0TuI+BsD0x4kGCuFSRVzSqkfiLiWmY17EALMbCAlMCmI6IwxZo+INgQYEYKBuW5da00PKikjhNNiiPGm01rrbwDwofGehQjjNcv1SZgddALhlJEgwgJFxDNr7acmjFLqCyJuTd6LEGFttpmkYC91Hrk3s1GZFERMmUT01Xv/sQljjPlMRMsxO6WULwnb2D8FEs4j680wScjO5f3vzrlNJszESWq2LYXJgTzjZm56MCHf3zVBxH1r7ftU1splxxKYHEgoUUpTo+grEf303rPH5hxENJqDKQEJtko2q9zGeeycWy3JhpKhWT8+NM/sufIhBwKI+Mta+7pkfxKMtd8Qtdbcx4dUQZcFCQ2I6DcAnLUpf6YMPxhIDDOuxC4C6djoQUE6+tKpewWZ1wlRkq0qUhXptKTlzv93aI3jWmE0Fz2TeujpX73F9TaKy9CeMk8vZusfBnqZ1g5GqyIdJq+XrqNR5AahKr9CCcxGSwAAAABJRU5ErkJggg==)](https://camo.githubusercontent.com/93bd445f511c0756f23e27fd6a1cbb0a8513b0396e8a802e5fdeb3ef66ce5278/68747470733a2f2f73332e75732d776573742d322e616d617a6f6e6177732e636f6d2f7365637572652e6e6f74696f6e2d7374617469632e636f6d2f32303534373766632d633964662d343866322d613831362d3530633838303966323434622f2545362539372541302545362541302538372545392541322539382e706e673f582d416d7a2d416c676f726974686d3d415753342d484d41432d53484132353626582d416d7a2d43726564656e7469616c3d414b49415437334c324734354f334b5335325935253246323032313038323125324675732d776573742d322532467333253246617773345f7265717565737426582d416d7a2d446174653d3230323130383231543035333830375a26582d416d7a2d457870697265733d383634303026582d416d7a2d5369676e61747572653d3931363030376462363635613039353630623863646535336331303438303337376131663538656564303561353766393938353334393664666236633837323926582d416d7a2d5369676e6564486561646572733d686f737426726573706f6e73652d636f6e74656e742d646973706f736974696f6e3d66696c656e616d652532302533442532322532354536253235393725323541302532354536253235413025323538372532354539253235413225323539382e706e67253232)
*   2.0.4: 彻底支持无论是默认英文还是韩文都会生效的汉化脚本（2021/08/19 油猴剧本 + win 客户端 + mac 客户端测试通过），统一 win mac 网页端实现。
*   2.0.3：支持切换到韩文之后帮助文档还原到默认英文版本
*   2.0.1：支持 mac 客户端（英文）
*   2.0.0: 支持 win 客户端（韩文） + 油猴脚本

[](#如何使用)如何使用?
==============

[](#网页端)网页端
-----------

1.  ### [](#安装油猴插件)安装油猴插件
    
    此处提供搜索到知乎的一篇教程：[https://zhuanlan.zhihu.com/p/128453110](https://zhuanlan.zhihu.com/p/128453110)
    
2.  ### [](#安装油猴脚本)安装油猴脚本
    
    打开链接：[https://greasyfork.org/zh-CN/scripts/430116-notion-%E5%AE%8C%E5%85%A8%E4%B8%AD%E6%96%87%E5%8C%96-%E5%9F%BA%E4%BA%8E%E9%9F%A9%E8%AF%AD%E7%89%88%E6%9C%AC-%E4%BD%BF%E7%94%A8%E8%85%BE%E8%AE%AFapi%E6%9C%BA%E7%BF%BB](https://greasyfork.org/zh-CN/scripts/430116-notion-%E5%AE%8C%E5%85%A8%E4%B8%AD%E6%96%87%E5%8C%96-%E5%9F%BA%E4%BA%8E%E9%9F%A9%E8%AF%AD%E7%89%88%E6%9C%AC-%E4%BD%BF%E7%94%A8%E8%85%BE%E8%AE%AFapi%E6%9C%BA%E7%BF%BB) 。然后点击安装。
    
3.  ### [](#体验汉化效果)体验汉化效果
    
    [https://www.notion.so](https://www.notion.so)
    

[](#桌面端)桌面端
-----------

**手动注入：**

### [](#windows)windows

1.  （自 **2.0.4** 版本后，任意语言都等价于中文了）
2.  notion 安装目录：`C:\Users\用户名\AppData\Local\Programs\Notion\`
3.  打开`C:\Users\用户名\AppData\Local\Programs\Notion\resources\app\renderer`文件夹
4.  下载 `notion-zh_CN.js` 到上述文件夹（renderer）
5.  打开 `preload.js`
6.  在最后一行加上
    
    ```
    //# sourceMappingURL=preload.js.map
     require("./notion-zh_CN") // 添加该行
    
    ```
    
7.  重启

*   上述操作也可以使用 PowerShell 命令来完成。  
    命令执行完成后，在 Notion 中使用 CTRL+R 可以热更新界面。
    
    ```
    Invoke-WebRequest -Uri "https://github.com/Reamd7/notion-zh_CN/releases/latest/download/notion-zh_CN.js" -OutFile "$HOME\AppData\Local\Programs\Notion\resources\app\renderer\notion-zh_CN.js"
    Add-Content "$HOME\AppData\Local\Programs\Notion\resources\app\renderer\preload.js" 'require("./notion-zh_CN")'
    
    ```
    

### [](#mac)Mac

网页端 以及 windows 端，能够 **100% 汉化**，指的是**时间显示也有国际化的能力**，点击所有更新的时间轴中就能看出来，点击？悬浮按钮也能看到。

1.  打开 Finder，应用程序，右键`notion.app`，显示应用包内容
2.  （自 2.0.4 版本后，任意语言都等价于中文了）
3.  打开 Notion.app\Contents\Resources\app\renderer\
4.  下载 `notion-zh_CN.js` 到上述文件夹（renderer）
5.  打开 `preload.js`
6.  在最后一行加上
    
    ```
    //# sourceMappingURL=preload.js.map
     require("./notion-zh_CN") // 添加该行
    
    ```
    
7.  重启

只是 同样打开 Notion.app\Contents\Resources\app\renderer\ 即可。。（安装包显示有同样目录结构）

[](#cloudflare-worker)cloudflare worker
---------------------------------------

> 不建议使用。不希望推广。有风险。你需要知道你在干什么。

1.  首页：[https://workers.cloudflare.com](https://workers.cloudflare.com)
    
2.  注册，登陆，`Start building`，取一个子域名，`Create a Worker`。
    
3.  复制 [worker.js](https://github.com/Reamd7/notion-zh_CN/blob/main/worker.js) 到左侧代码框，修改
    
    ```
    const BaseUrl = "xxxx.子域名.workers.dev" // 修改为自己的子域名
    
    ```
    
4.  `Save and deploy`。如果正常，右侧应显示提示框： Mismatch between origin and baseUrl (dev). 好的（这里就证明汉化成功了）
    
5.  以后可直接访问 `https://xxxx.子域名.workers.dev`。
    

[](#安卓端)安卓端
-----------

*   下载 apk：[https://github.com/Reamd7/notion-zh_CN/blob/main/apk/Notion_0.6.160_zh_cn.apk](https://github.com/Reamd7/notion-zh_CN/blob/main/apk/Notion_0.6.160_zh_cn.apk)
*   或者下载这个压缩包然后解压：

[Notion_0.6.160_zh_cn.apk.7z](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a2c28ec1-416d-4429-8133-56a20ff435d6/Notion_0.6.160_zh_cn.apk.7z)

[](#大家可以做什么)大家可以做什么？
====================

1.  **优化汉化语言**。都是机器翻译，看到不通畅的句子欢迎提 issue/pr 直接改了 （修改 **`json/zh.json`** 文件，了解之前，先找到原有的英文，韩文对照一下再更新翻译。）

[](#呼吁)呼吁：
==========

提高付费率，支持你所支持的软让他发展更好，这样国内市场才会更受重视，而不是只是白嫖，买淘宝，搞教育账户。

[](#star-history)Star History
-----------------------------

[![](https://camo.githubusercontent.com/5cbe7a635c1fecd1548cb2692b4978ce42c4737d8d11a32091b58d0d20c21a34/68747470733a2f2f6170692e737461722d686973746f72792e636f6d2f7376673f7265706f733d5265616d64372f6e6f74696f6e2d7a685f434e26747970653d44617465)](https://star-history.com/#Reamd7/notion-zh_CN&Date)