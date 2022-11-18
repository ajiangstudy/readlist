> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.52pojie.cn](https://www.52pojie.cn/thread-1714704-1-1.html)

> 【原理简介】[*] 首先，微信 DAT 文件是将图片数据的每个字节经过和密钥做异或运算来得到的。

![](https://avatar.52pojie.cn/images/noavatar_middle.gif)xue5hen 【原理简介】  

*   首先，微信 DAT 文件是将图片数据的每个字节经过和密钥做异或运算来得到的。
*   异或运算法则：如果 a、b 两个值不相同，则异或结果为 1。如果 a、b 两个值相同，异或结果为 0。
*   异或运算有个可交换的特点，即：如果 a 和 b 异或运算后得到了 c，那么在 a、b、c 三者中，任意两者进行异或运算会得到它们中的第三者。  
    

  
  
  基于上面三条来梳理一下工具编写的前提条件，就变成了下面表格描述的这样。问题变得简单了，我们只需要通过循环，将图片的文件头数据的第 1、2 字节与 DAT 数据的第 1、2 字节相应做异或运算，那么就可以得到两个值，如果这两个值相等，那么就是我们要找的密码。然后用得到的密码与 DAT 的所有字节做异或运算，便可以还原出原始的图片文件。  
<table cellspacing="0"><tbody><tr><td>图片</td><td>密码</td><td>DAT</td></tr><tr><td><br>可有限枚举，已知文件头数据<br>jpg: [0xFF, 0xD8, 0xFF]<br>png: [0x89, 0x50, 0x4E]<br>gif: [0x47, 0x49, 0x46]<br>...</td><td>未知</td><td>已知</td></tr></tbody></table>  
     
【工具编写】  
  基于上述原理，代码实现起来并不难。我用 JS 写了两个版本，一个 Electron 版本的，一个是 Web 版本的。相对而言，Electron 打包后体积较大，对于一个功能单一的小工具来讲太鸡肋；而 Web 版本比较轻量，而且可以挂到网上，随时随地方便地使用，性价比更优。  
  如下图所示，工具的界面设计比较简单，Web 版本只有一个主区域，可以将 DAT 文件拖拽进去还原出图片，因为文件头枚举数量很少，所以速度很快，基本是瞬间的；下方设置了两个按钮 “全部删除” 和“全部下载”，可以快速清空主体区域和下载所有还原出来的图片。  
![](https://attach.52pojie.cn/forum/202211/17/220258c22zphycbc47icy7.png)

**Electron.png** _(489.13 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU3MDEwMHxlNDRhMGQ5ZXwxNjY4Nzc3Njg5fDEwMDI4MzR8MTcxNDcwNA%3D%3D&nothumb=yes)

2022-11-17 22:02 上传

  
![](https://attach.52pojie.cn/forum/202211/17/220300qz6zehrqoz9vesoe.png)

**web.png** _(127.88 KB, 下载次数: 0)_

[下载附件](forum.php?mod=attachment&aid=MjU3MDEwMXw2MDMyNDc4MXwxNjY4Nzc3Njg5fDEwMDI4MzR8MTcxNDcwNA%3D%3D&nothumb=yes)

2022-11-17 22:03 上传

  
  代码逻辑并不复杂，这里贴两处比较关键的代码片段（Web 版），文后会附上 Web 版的下载地址，另外也做了个视频（两个版本的工具展示 + 代码解释），可以视自己口味选择下载和观看。  
  [JavaScript] _纯文本查看_ _复制代码_

```
// 拖拽添加文件drop (e) {
  const fileList = e.dataTransfer.files
  if (!fileList) return
  // 取文件后缀名，必须是dat文件
  let taskList = []
  let indexList = []
  for (let i = 0; i < fileList.length; i++) {
    const file = fileList[i]
    if (!/.dat$/i.test(file.name)) {
      return this.$toast('请选择DAT文件！')
    }
    let fStat = fs.statSync(file.path)
    if (fStat.isDirectory()) {
      return this.$toast('请选择DAT文件！')
    }
    taskList.push(this.getFileInfo(file.path))
    indexList.push(i)
  }
  Promise.all(taskList).then((infos) => {
    if (!infos || !infos.length) return
    infos.forEach((v, i) => {
      let file = fileList[indexList[i]]
      this.filesList.push({
        name: file.name, path: file.path, size: file.size, ...v
      })
    })
  })
}

```

  [JavaScript] _纯文本查看_ _复制代码_

```
// 获取单个文件的信息（包括密码和数据解密）getFileInfo (filePath) {
  let result = {name: '', type: '未知', password: '', data: '', url: ''}
  let _arr = path.basename(filePath).split('.')
  result.name = _arr.slice(0, _arr.length - 1).join('.')
  return new Promise((resolve, reject) => {
    if (!fs.existsSync(filePath)) {
      reject('文件不存在')
    }
    fs.readFile(filePath, (err, data) => {
      if (err || !data) reject('读取文件错误')
      result.data = data
      for (let key in this.fileHeaderMarks) {
        let val = this.fileHeaderMarks[key] || []
        let pwd1 = (val[0] || 0) ^ data[0]
        let pwd2 = (val[1] || 0) ^ data[1]
        if (pwd1 === pwd2) {
          result.type = key
          result.password = pwd1
          break
        }
      }
      if (result.password) {
        let mimeType = this.fileMimeType[result.type] || `image/${result.type}`
        result.data = result.data.map(v => (v ^ result.password))
        result.url = `data:${mimeType};base64,${result.data.toString('base64')}`
      }
      resolve(result)
    })
  })
}

```

  视频展示：https://www.bilibili.com/video/BV1f841187tm/  
  Web 版工具源码：https://pan.baidu.com/s/1_KIqd0h_3T2vcR87GlUJYg?pwd=3m4h 提取码: 3m4h![](https://avatar.52pojie.cn/images/noavatar_middle.gif)xue5hen

> [nuxingxp 发表于 2022-11-18 20:19](https://www.52pojie.cn/forum.php?mod=redirect&goto=findpost&pid=44777950&ptid=1714704)  
> 楼主，达到您的水平，得学哪些课程？

前端开发相关的课程：html、css、js、jQuery、vue 全家桶（或 React）、nodejs、electron 这些 ![](https://avatar.52pojie.cn/data/avatar/000/49/89/99_avatar_middle.jpg) nuxingxp

> [xue5hen 发表于 2022-11-18 20:54](https://www.52pojie.cn/forum.php?mod=redirect&goto=findpost&pid=44778296&ptid=1714704)  
> 前端开发相关的课程：html、css、js、jQuery、vue 全家桶（或 React）、nodejs、electron 这些

这么多，够呛了。谢谢楼主。 ![](https://avatar.52pojie.cn/images/noavatar_middle.gif) 思路清晰，出个聊天记录版吧大佬![](https://avatar.52pojie.cn/images/noavatar_middle.gif)已经好晕了 看不懂多多学习谢谢 ![](https://avatar.52pojie.cn/images/noavatar_middle.gif) baohe 暂时还看不明白，努力！![](https://avatar.52pojie.cn/images/noavatar_middle.gif)shf8799 大佬大佬![](https://static.52pojie.cn/static/image/smiley/default/17.gif) ![](https://avatar.52pojie.cn/images/noavatar_middle.gif) chen0jay 感谢分享，好用 ![](https://avatar.52pojie.cn/images/noavatar_middle.gif) wxq_hz ![](https://static.52pojie.cn/static/image/smiley/default/42.gif)请收下膝盖![](https://avatar.52pojie.cn/images/noavatar_middle.gif)Michael_Yang 学习学习，谢谢楼主 ![](https://avatar.52pojie.cn/images/noavatar_middle.gif) faith9527 估计出个聊天记录会更火 ![](https://avatar.52pojie.cn/data/avatar/000/35/06/45_avatar_middle.jpg) Q17 ![](https://static.52pojie.cn/static/image/smiley/laohu/laohu11.gif)好强，感谢大佬分享