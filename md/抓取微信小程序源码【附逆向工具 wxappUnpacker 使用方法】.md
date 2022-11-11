> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.52pojie.cn](https://www.52pojie.cn/thread-1708787-1-1.html)

> 文章目录 [*] 前言 [*] 一、工具准备（免费）[*]1 解密工具 [*]2 逆向工具[*] 二、解密小程序[*]1. 确认小程序包位置[*]2. 打开一个小程序[*]3. 解密小程序包 ... 抓取微信小程序源码【......

![](https://avatar.52pojie.cn/data/avatar/000/40/25/09_avatar_middle.jpg)why3316 **文章目录**

*   前言
*   一、工具准备（免费）  
    *   1 解密工具
    *   2 逆向工具  
        
*   二、解密小程序  
    *   1. 确认小程序包位置
    *   2. 打开一个小程序
    *   3. 解密小程序包  
        
*   三、逆向小程序  
    *   1、检查 nodejs
    *   2、安装依赖
    *   3、正式逆向  
        

**前言**  
想成为一名微信小程序的开发者，**前端思路的学习和安全意识是非常有必要的**，故**务必掌握小程序反编译技能。**这里用到了 2 个工具《解密》与《逆向》（非原创，均来自网上的大佬），**特别适合新手，而且都是免费的！都是****免费的！都是免费的！**第一次操作可能会慢一些，熟练了之后，**3 秒抓取一个小程序源码！****  
一、工具准备（免费）****  
1、解密工具**  
![](https://attach.52pojie.cn/forum/202211/06/183913y444xqkm6oq22iio.png)

**1.png** _(16.58 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU2NTY3M3xlNTA4NzhkM3wxNjY4MTI0ODQyfDEwMDI4MzR8MTcwODc4Nw%3D%3D&nothumb=yes)

2022-11-6 18:39 上传

  
下载地址：https://www.aliyundrive.com/s/8L9WzXPzXPE 提取码: 75mz  
**  
2、逆向工具**  
目前用的是：wxappUnpacker  
![](https://attach.52pojie.cn/forum/202211/06/183941gkl7xgn4nx61zzlg.png)

**2.png** _(60.21 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU2NTY3NHw1ZjM5NzgxMHwxNjY4MTI0ODQyfDEwMDI4MzR8MTcwODc4Nw%3D%3D&nothumb=yes)

2022-11-6 18:39 上传

  
这个是一个大神开发的，之前可以在 github 下载，不过截止今天，大神已经关闭了下载，具体原因…… 你懂得。不过，开源是趋势，就像这个世界是不会停止开放的，因此我们还是有很多渠道可以获取，你可以通过自己的渠道获取，或者用我为你准备好的：  
下载地址：https://www.aliyundrive.com/s/DSgSNq7GAJR 提取码: l99u  
**  
二、解密小程序  
**网上有很多教程，是分苹果和安卓的，还要用到模拟器，其实不用那么麻烦，直接用微信 PC 客户端就可以了。  
**  
1. 建议修改微信 PC 端默认的小程序包位置  
**默认是在 C 盘，太占内存，建议修改  
![](https://attach.52pojie.cn/forum/202211/06/184005a3tffs837stj5t8f.png)

**3.png** _(69.68 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU2NTY3NXw3MWQ1Y2M4OHwxNjY4MTI0ODQyfDEwMDI4MzR8MTcwODc4Nw%3D%3D&nothumb=yes)

2022-11-6 18:40 上传

  
**2. 打开一个小程序**在 pc 端打开一个小程序，尽可能点开所有的页面，让本地自动生成一个本地包，在刚刚设置好的文件夹里：  
![](https://attach.52pojie.cn/forum/202211/06/184007tn9j1y29h932x082.png)

**4.png** _(20.29 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU2NTY3NnwyODkwOTRlMnwxNjY4MTI0ODQyfDEwMDI4MzR8MTcwODc4Nw%3D%3D&nothumb=yes)

2022-11-6 18:40 上传

  
不过里面的是加密过的文件：__APP__.wxapkg 就需要用到我们前面的解密软件。  
**  
3. 解密小程序包  
**软件长这样：  
![](https://attach.52pojie.cn/forum/202211/06/184009yw1xush1ssz77u03.png)

**5.png** _(13.28 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU2NTY3N3w2ZDc2ZTdjZnwxNjY4MTI0ODQyfDEwMDI4MzR8MTcwODc4Nw%3D%3D&nothumb=yes)

2022-11-6 18:40 上传

  
**选择加密小程序包**  
![](https://attach.52pojie.cn/forum/202211/06/184011k6karzzzh63yzn6g.png)

**6.png** _(15.72 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU2NTY3OHxkNjlhYWY4MnwxNjY4MTI0ODQyfDEwMDI4MzR8MTcwODc4Nw%3D%3D&nothumb=yes)

2022-11-6 18:40 上传

  
0.1 秒解密成功：  
![](https://attach.52pojie.cn/forum/202211/06/184013j777y7m7577x79q9.png)

**7.png** _(14.21 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU2NTY3OXxiNjQzMWY5YnwxNjY4MTI0ODQyfDEwMDI4MzR8MTcwODc4Nw%3D%3D&nothumb=yes)

2022-11-6 18:40 上传

  
**解密之后的文件名是：**  
[Asm] _纯文本查看_ _复制代码_

```
wx4f110483368dc766.wxapkg

```

**会存放在 wxpack 文件夹：**  
![](https://attach.52pojie.cn/forum/202211/06/184016er7wcrwdzcwo6tzr.png)

**8.png** _(19.97 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU2NTY4MHw2OWIzODEwNXwxNjY4MTI0ODQyfDEwMDI4MzR8MTcwODc4Nw%3D%3D&nothumb=yes)

2022-11-6 18:40 上传

  
**三、逆向小程序**正式用到大神开发的【wxappUnpacker】了。下面的操作，都是在 cmd 命令窗口中操作的，需要强调的是，必须在 wxappUnpacker 路径里才可以，简易方法是，直接在【wxappUnpacker】文件夹的地址栏里输入 cmd 即可。  
![](https://attach.52pojie.cn/forum/202211/06/184018sriaronz88iuumr8.png)

**9.png** _(27.35 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU2NTY4MXw3YTA1ODA2Y3wxNjY4MTI0ODQyfDEwMDI4MzR8MTcwODc4Nw%3D%3D&nothumb=yes)

2022-11-6 18:40 上传

  
**如果跟我一样放在桌面，出来的就是这样：**  
![](https://attach.52pojie.cn/forum/202211/06/184020g26zr6hw5r0680z2.png)

**10.png** _(12.58 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU2NTY4Mnw4OGI3ZDA2ZHwxNjY4MTI0ODQyfDEwMDI4MzR8MTcwODc4Nw%3D%3D&nothumb=yes)

2022-11-6 18:40 上传

**  
  
1、检查 nodejs  
**输入 node -v 检查是否已安装 nodejs  
![](https://attach.52pojie.cn/forum/202211/06/184022tzssy0ll6z885lvd.png)

**11.png** _(11.73 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU2NTY4M3w4MWEyNjZlNXwxNjY4MTI0ODQyfDEwMDI4MzR8MTcwODc4Nw%3D%3D&nothumb=yes)

2022-11-6 18:40 上传

  
如果没有安装 nodejs，请先安装。下载地址：[https://nodejs.org/en/](https://nodejs.org/en/) 安装 nodejs 一直点击下一步安装即可。  
**  
2、安装依赖  
**依次输入下面 7 个 npm install，分别一个一个安装  
[Asm] _纯文本查看_ _复制代码_

```
npm install
npm install esprima
npm install css-tree
npm install cssbeautify
npm install vm2
npm install uglify-es
npm install js-beautify

```

![](https://attach.52pojie.cn/forum/202211/06/184024b2fcz2r7axzrirpq.png)

**12.png** _(17.83 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU2NTY4NHw3ZWE3ZThhY3wxNjY4MTI0ODQyfDEwMDI4MzR8MTcwODc4Nw%3D%3D&nothumb=yes)

2022-11-6 18:40 上传

  
**  
3、正式逆向  
**输入：[Asm] _纯文本查看_ _复制代码_

```
bingo.bat 主包路径（可以直接拖入）

```

![](https://attach.52pojie.cn/forum/202211/06/184026nlsxn8htssgrgrnl.png)

**13.png** _(25.38 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU2NTY4NXw1N2U4MjhlMHwxNjY4MTI0ODQyfDEwMDI4MzR8MTcwODc4Nw%3D%3D&nothumb=yes)

2022-11-6 18:40 上传

  
编译后的文件，保存在和【wx4f110483368dc766.wxapkg】同一个文件夹中，自动以 wx4f110483368dc766 命名。  
![](https://attach.52pojie.cn/forum/202211/06/184028bs4jghes4fgxfj1j.png)

**14.png** _(35.14 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU2NTY4Nnw0ZDZmMjhhNHwxNjY4MTI0ODQyfDEwMDI4MzR8MTcwODc4Nw%3D%3D&nothumb=yes)

2022-11-6 18:40 上传

  
OK，编译完成，接下来直接使用微信开发工具打开，即可学习前辈们的前端设计了，骚年。  
**  
4、可能的错误****  
①、如果在执行编译命令时报  
**[Asm] _纯文本查看_ _复制代码_

```
this package is a subPackage which should be unpacked with -s=. 
```

说明这个是分包，打开小程序时生成了两个. wxapkg 文件，编译另一个文件即可，编译分包和主包的命令是不一样的：  
[Asm] _纯文本查看_ _复制代码_

```
node ./wuWxapkg.js 分包路径 -s=主包路径

```

**  
②、如果生成的文件里不包含 app.json 文件  
**说明你找的小程序，是大神开发的，已经做了反编译的安全措施，所以解密失败，这也是我发这篇文章的目的。  
**不过这种大神目前还是比较少见的，你会成为未来的那一个吗？加油，骚年，欧力给！**  
![](https://attach.52pojie.cn/forum/202211/06/184030ov7fidgxysh1ex71.png)

**15.png** _(69.23 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU2NTY4N3w3ZjhkMGQ5OHwxNjY4MTI0ODQyfDEwMDI4MzR8MTcwODc4Nw%3D%3D&nothumb=yes)

2022-11-6 18:40 上传

**  
  
四、结束语  
**好了，微信小程序反编译教程 + 解包教程 + 解包工具的使用，已经为大家分享完毕；  
**PS：**喜欢这个帖子的，动动你发财的贵手，点击 “评分” 按钮给个**免费**评分，**觉得这个帖子对你有用的，点击评分旁边的 “有用” 按钮，让更多人看到，谢谢！** ![](https://avatar.52pojie.cn/images/noavatar_middle.gif)h012031 [分享] 反编译微信小程序获取小程序前端源码 wxapkg  
发表于 2021-7-10 13:17  
[https://www.52pojie.cn/forum.php ... 5%D0%A1%B3%CC%D0%F2](https://www.52pojie.cn/forum.php?mod=viewthread&tid=1473679&highlight=%CE%A2%D0%C5%D0%A1%B3%CC%D0%F2)![](https://avatar.52pojie.cn/images/noavatar_middle.gif)fanxuebin 能抓取小程序服务端源码就更好了，哈哈 ![](https://avatar.52pojie.cn/data/avatar/000/20/15/05_avatar_middle.jpg) Eaysuild.xean ![](https://static.52pojie.cn/static/image/smiley/default/31.gif)老哥图片全挂 ![](https://avatar.52pojie.cn/data/avatar/001/05/71/65_avatar_middle.jpg) GMCN 图片看不了，麻烦原地址发一下![](https://avatar.52pojie.cn/images/noavatar_middle.gif)levi1005 图片挂了大哥，想学下![](https://avatar.52pojie.cn/images/noavatar_middle.gif)波妞阿姨 图片挂了老板。![](https://avatar.52pojie.cn/images/noavatar_middle.gif)kangok 感谢分享，跟随学习 ![](https://avatar.52pojie.cn/images/noavatar_middle.gif) xiaolong666 逆向微信小程序眼 ![](https://avatar.52pojie.cn/images/noavatar_middle.gif) xcz668 有视频教程就好了![](https://avatar.52pojie.cn/images/noavatar_middle.gif)落神 全挂了老板