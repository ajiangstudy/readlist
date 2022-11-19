> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.zhihu.com](https://www.zhihu.com/question/448807187/answer/2251389215)

> 近日 Notion 的开源替代品 AppFlowy 正式发布了，一经发布，在短短一周就获得了近 8k Star。这个成绩对于…

![](https://pic1.zhimg.com/v2-d41c2ceaed8f51999522f903672a521f_l.jpg?source=1940ef5c)匿名用户

近日 Notion 的开源替代品 AppFlowy 正式发布了，一经发布，在短短一周就获得了近 8k Star。

![](https://pic1.zhimg.com/v2-a543f349965bf5dae5c3b37262621fe0_r.jpg?source=1940ef5c)

这个成绩对于一个开源项目来说是非常不错的，那么为什么有了 Notion ，AppFlowy 团队却要从头开始开发一个类似的产品呢？

这主要是源于 Notion 的一些局限包括：[数据安全](https://www.zhihu.com/search?q=%E6%95%B0%E6%8D%AE%E5%AE%89%E5%85%A8&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A2251389215%7D)、移动端适配等等原因。

即使 Notion 是 AppFlowy 团队最喜欢的项目以及知识管理工具，但是在一些企业的场景中，数据安全以及数据的 100% [私有化管理](https://www.zhihu.com/search?q=%E7%A7%81%E6%9C%89%E5%8C%96%E7%AE%A1%E7%90%86&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A2251389215%7D)是非常重要的。

AppFlowy 团队希望通过三个最基本的价值观来实现这一使命：  
1. 数据隐私第一  
2. 可靠的原生体验  
3. 社区驱动的可扩展性

基于以上的问题的，AppFlowy 诞生了，虽然 AppFlowy 团队谦虚的说：并没有打算在功能和设计上超过 Notion ，他们现阶段的任务只是培养一个社区，为制作一个复杂的工作管理工具积累经验和知识。同时能为个人和企业创建更加优秀的管理工具而奠定基础。看来 AppFlowy 团队有着非常宏大的理想和目标，想要让一个产品能更加成功，就要发挥尽可能对其感兴趣的力量，当年的 Linux 不正是如此？

我们来看看 AppFlowy 的主页以及相关的截图:  

![](https://pic1.zhimg.com/v2-d17a5c1351487e68b62a2420ce37b996_r.jpg?source=1940ef5c)![](https://picd.zhimg.com/v2-5b8d8f292b7522af2d9a4181bba08d61_r.jpg?source=1940ef5c)![](https://pica.zhimg.com/v2-d3daca3c2bd734d5aa3986cf0fdc11f2_r.jpg?source=1940ef5c)

看起来非常的不错，但是目前 github 上没有提供安装来进行体验，想要体验必须通过开发环境下来进行体验，作为程序员，安装启动程序还是不在话下的 :) ，毕竟本博主精通各种语言的安装以及输出 "Hello World"。

AppFlowy 是有 Flutter 和 Rust 开发的，这使得他的跨平台能力和性能都有了一定程度保障。  
先来看看 README 的启动介绍吧~  

![](https://picd.zhimg.com/v2-ce99cc267f82ee94d0816bd18164c560_r.jpg?source=1940ef5c)

第一步和第二步都比较简单。  

![](https://pic1.zhimg.com/v2-bfacfb8b837e0ae9b8a1903eb6c7b518_r.jpg?source=1940ef5c)

到了第三步，由于需要安装 Flutter，稍微有点麻烦，需要安装 Flutter，不过幸好中文版 Flutter 教程中已经为了我们提供了教程已经[镜像源](https://www.zhihu.com/search?q=%E9%95%9C%E5%83%8F%E6%BA%90&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A2251389215%7D)的更换，可以通过以下教程安装好 Flutter：[https://flutter.cn/community/china](https://link.zhihu.com/?target=https%3A//flutter.cn/community/china)

  
接下来还需要安装好 Android Studio 以及 Xcode。

Android Studio 安装教程：[https://sevencho.github.io/archives/67c8fe48.html](https://link.zhihu.com/?target=https%3A//sevencho.github.io/archives/67c8fe48.html)

  
Xcode 必须要 12.1 版本以上，直接 App Store 下载升级即可。不过我的 Mac OS 版本比较低，因此特地为了安装，升级了 `MacOS Catalina`， `Big Sur` 下载完安装不上（可能是机型太老了。）  

![](https://picd.zhimg.com/v2-ad5e0dcb3f16c94b735ff2a520d5fb4a_r.jpg?source=1940ef5c)

进入 Android Studio Manager 安装 [cmdline-tools](https://www.zhihu.com/search?q=cmdline-tools&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A2251389215%7D)，证书直接按照提示运行即可。  

![](https://pic1.zhimg.com/50/v2-da43d8637f1e9f91ffebf41c23caae41_720w.jpg?source=1940ef5c)

中间安装证书遇到一个问题，解决方案：  
[https://segmentfault.com/a/1190000021926094](https://link.zhihu.com/?target=https%3A//segmentfault.com/a/1190000021926094)

  
最后由于不清楚 flutter 如何运行，花了好久查了资料，原来运行以上四步后，还需要运行  
flutter run -d macOS

![](https://picd.zhimg.com/v2-965f5c617460ccc2784eb68495a6786e_r.jpg?source=1940ef5c)

  
最终我们可以看到整个应用跑起来了：

![](https://picd.zhimg.com/v2-cef696585911d3b82b70f0d9adda119c_r.jpg?source=1940ef5c)

试了一下目前的版本，主要还是呈现一个 md 编辑器的状态，并且还有一些 BUG，一些快捷键都没有支持，还是比较一个基础的应用~

不过 AppFlowy 团队也制定了一些规划公开在 trello 上面，并且有每一个规划的截图（感觉这样的方式很不错，准备也写一个木及简历的规划并且公开）  

![](https://picd.zhimg.com/v2-251935c98d4fc2f14b5e4c1a993309f3_r.jpg?source=1940ef5c)

长期目标主要有，[离线模式](https://www.zhihu.com/search?q=%E7%A6%BB%E7%BA%BF%E6%A8%A1%E5%BC%8F&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A2251389215%7D)、协作、设计系统、移动端 app、面板和同步等等功能。短期主要是拖拽以及快捷工具栏。

Notion 是一个很优秀的产品，但是 AppFlowy 有了开源的力量之后，相信未来肯定会非常有潜力，并且大家也可以学习这款产品背后的技术，相信会有一个极大的提升。

看到一些 Notion 「[开源替代产品](https://www.zhihu.com/search?q=%E5%BC%80%E6%BA%90%E6%9B%BF%E4%BB%A3%E4%BA%A7%E5%93%81&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A2251389215%7D)」的出现，你有什么期待呢~

![](https://pica.zhimg.com/v2-96b59984394054cb57d59b1e9ec8ee7e_l.jpg?source=1940ef5c)普通 NPC

你的英语已经弱到不会用英语提问了吗

![](https://pica.zhimg.com/v2-d41c2ceaed8f51999522f903672a521f_l.jpg?source=1940ef5c)匿名用户

这个问题的提问者就是典型的 “人上人” 心态，

这种心态在 Notion 的 telegram 小组特别严重，

在这个小组中，曾有人表达对索要中文者的不屑，表示这些人都不善学习，可问题是作为母语是中文的人来说，不是不学习，不懂基础英语，而是中文效率会更高。不然 wolai 为什么会对中文极致优化。这是一个习惯上的效率的提升，细节的优化带来的软件传播的便利、广泛化（举个例子，比如我需要和某个人一起做学习上的项目管理，我采用 Microsoft project，当我分享给他使用的时候我需要考虑他的上手速度，学习成本等，如果他并不知道如何使用，如言语障碍，学习难度等，我会弃用这个软件，况且 Notion 本身特别适合云协作），而不是单纯的语言障碍问题。所以提出为什么没有中文版并不是说连英语都舍不得学，舍不得学的还会用效率软件提高自己效率吗？估计连软件都懒得打开，直接卸载都不会问有没有英语的事。不如说提出这个问题的人根本不动脑更贴切。

我非常赞同回答者 Kevin 的回答。这才是大多数需求者的想法。

![](https://picd.zhimg.com/v2-cec3189bb7ea8892001fde4178ac547b_r.jpg?source=1940ef5c)![](https://pic1.zhimg.com/v2-43824341c5b6ab1c3ca6cca859e1f058_r.jpg?source=1940ef5c)

我知道翻译一个东西本身是一件很难的事，况且作为 Notion 的翻译还是为爱发电，但是这应该是翻译者和我们对话，来表达他们的立场。而不是很多无关痛痒的人来抱怨为什么有的人需要中文这种事。也不需要很多自我认为我们做为需求者把要中文这种事上升到国家民族的人。

小组里曾提及中文上百次才想到说发布公告来说明中文的事情。我总觉得说，不能因为读书就不吃饭了，你选择加入中文翻译就应该有责任。否则不应该加入。不然之间的误会、矛盾会减少很多。

（说个题外话，一个企业的中文翻译需要有人为爱发电才能出来，我觉得挺离谱的，况且 Notion 不差钱）

————————

之前 Notion 有出现过优惠上被薅羊毛的事，群里第一时间不是倡导理智看待或者表示不要这样做，而是专门开视频会议来讨伐 off topic 行为来表达不满，封住人的嘴。有问题提出来就行了，还要专门开会议阴阳怪气，管理员职责当放屁。我称这种就是资本主义上层阶级的圆桌会议，自我娱乐。

小组里个别成员或者有少数个别管理是自我高尚者，其中不乏提问者这种，部分话语被定性，且回答有阴阳怪气的嫌疑

![](https://pic1.zhimg.com/v2-893c1a5a155b8d5fce005a2671263c9e_r.jpg?source=1940ef5c)

连笔记的用法和使用经验交流都被抵制，这不是交流群吗？真的恶臭。我并不是那个提问的，但我觉得回复过于恶臭了。

而且管理员选择性忽视 off topic 行为，并加入其中

![](https://pic1.zhimg.com/v2-f8b31afac2280dc04fd0ec13a99ee980_r.jpg?source=1940ef5c)

我说这些是想说，Notion 是好软件，每个笔记也有自己的优点，不是你 Notion 不错，使用的人就很牛，很高尚，别把自己当奢侈品柜姐看不起别人，在我眼里就是鸡。特别典型的就是提出非要中文疑问的这个提问者。

这社会上有不懂英语的，但有心学习的，有不懂操作的，有想理解别人软件使用想法和经验的，各种人都有，但说到底，他有使用软件的权利，表达合理诉求的权利，不赞成的话，求同存异就好，不想 回答为什么的话，避开不谈就好，硬要彰显自己独特的，怼人的，唯有用 Notion 的某些人特别出众。

—————