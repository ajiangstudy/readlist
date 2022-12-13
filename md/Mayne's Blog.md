> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [gine.me](https://gine.me/posts/0f9bfeceeaad42649ef70c54d8fdffa6)

> Mayne's Blog

notion 的付费用户可以无限制的上传图片，那么你的私人图床就来了。

优缺点
---

**优点**

**缺点**

*   内容可控。增删改查都可以自己来。
    
*   服务稳定。你付钱给 notion，notion 付钱给亚马逊。无限存储（目前看来），比公共图床稳定多了。
    
*   **访问**不稳定。由于众所周知的原因，亚马逊的图片服务访问不怎么稳定，因为地区和网络环境的差异，有些地方或时间段可能无法正常访问（除了偶尔抽风，大部分时间都正常）
    

构建一个图床
------

1.  创建表格，最好是网格视图，就像下面这样。你完全不需要配置任何东西。
    
2.  确保你的表格页面是公开的，其它人可以访问的。
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f092aa2e-0fbb-4ff8-bad2-492f69eed61a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20221213%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20221213T092011Z&X-Amz-Expires=3600&X-Amz-Signature=4805c780e5313997c3761cb42af26a394e850e940d52a6d6ec45ee6a2e0ee254&X-Amz-SignedHeaders=host&x-id=GetObject)
    
3.  将图片拖入其中，自动就上传好了
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/82a6bf7d-a7d0-47d4-bc94-7b8bc9aee1c2/notion-images-demo.gif?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20221213%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20221213T092012Z&X-Amz-Expires=3600&X-Amz-Signature=12fd73157dd8f17bb2163ca671e05e377a479a87eed992f4c0bbc5d4d1bc3126&X-Amz-SignedHeaders=host&x-id=GetObject)
    
4.  **在隐身窗口下打开图床页面**，点开图片，右键复制图片链接即可
    

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/44b49c0d-ed51-4eb1-856e-a7780d7b369d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20221213%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20221213T092010Z&X-Amz-Expires=3600&X-Amz-Signature=0191340133e904b71a6320195f34bf3e2617c7c910acb3810f8d4d870506e743&X-Amz-SignedHeaders=host&x-id=GetObject)

外链注意事项
------

*   notion 使用的是亚马逊的存储服务。如果你以登录用户访问，查看图片时，链接是这样的
    
    ```
    https://s3.us-west-2.amazonaws.com/secure.notion-static.com/20d5720f-ff62-47f7-a827-7ea17ed9fba8/untitled?AWSAccessKeyId=ASIAT73L2G45O4BCQ4JZ&Expires=1551528594&Signature=Ns%2BKYeSR%2FBhkezc8MF8lPNgnTow%3D&response-content-disposition=filename %3D"untitled"&x-amz-security-token=FQoGZXIvYXdzEPr%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDISznguQKC3MwayxlCK3A%2BV3a%2FMYCX09A8pvHzq3xXZzYC4d6x9zYYOrFqFAps0Yj8dgwL3eSQxH9NOpGc3OXjF0YFfcnhPp2U4p6XVKtAAi4lMsotKtrIGmqWBwEFbwSr%2FE9wueXOAv4UJMsL%2BPZyIdzwvkGR7PlGV9ftDozBPOHmHJApi7MxzehqWKlF9A%2FIoCKAGzvcQldSMJSbE%2FMkEksPeW1215McWUYP%2Fn%2FnpPi8hqWw5GqA3bnNZ%2BSxLe2eFKTJtByC%2FtkDsqTTqlmLo7HJqfN4RmyvHw11V6tuuL25lmr3C1mnhjaN1ZNoN1opmalcwcRj%2F1UmDprDRbhVCgq%2FIgtq4XPuubROk5V%2FQyCq9MS%2FYeeqAn2lsSAdFBEmmUrRSz1v%2Fa1SuwasPirZuMOrYi2fs4zAlByK5dYsoPRCwKzjCg7oDfa2%2BpkKl0rqHEx8WhEHvgK%2F7BZmCIHmuaqX1ppQ4ZGum22RFecYnO7xx1cbTmbBUuK3MGRGCUxsG0vXqWldD13kpMFlVsR7VXa3RaJHKZMfr8nbjnbJWvTKfGPDKamcJCAaKjcngbW9mETi%2B%2BvT%2FQf9WOSKzmkWMWFD4uoTYoqt3j4wU%3D
    
    
    ```
    
*   该链接有访问过期时间。所以当你把这个链接分享给别人时，过段时间可能就没法访问了。
    
*   隐身窗口下访问的图片链接是这样的
    
    ```
    https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F409273bd-a5ee-4045-8363-6723795858c9%2Fmy-octocat-1544438897338.png?width=1930
    
    
    ```
    
    ```
    https://www.notion.so/image/原亚马逊链接存储链接（做一点处理）?width=宽度
    
    
    ```
    
    通过控制宽度参数，可以获取自己想要 size 的图片。
    
    注意这里不可以直接通过 做转换。`encodeURIComponent（原始url）`
    
    转换后的链接应该是 s3-us-west-2 ，而不是 s3.us-west-2
    
    转换代码如下
    
    ```
    openUrl = encodeURIComponent("原图链接（不带token参数的）"）.replace("s3.us-west-2","s3-us-west-2")
    
    
    ```
    
*   在 aws 域下的图片都是带有 token 的，存在过期时间。所以图片链接无法作为固定链接使用，需要做上面提到的转换。
    
*   简单来说。非登录用户看到的图片链接有 2 种形式
    
    1.  png/jpeg / 其它待考证的格式 —— 图片属于 notion 域下，可作为长期固定链接使用
    2.  gif / 视频 / 其它待考证的格式—— 资源属于 aws 域下，携带 token 访问，不可直接作为固定链接，需要转换后才能使用。

详细转换代码参见

[https://github.com/mayneyao/notabase/blob/7aa5b10bf8992b0b586e98a56df5a41b95ce8c6c/src/utils.js#L37](https://github.com/mayneyao/notabase/blob/7aa5b10bf8992b0b586e98a56df5a41b95ce8c6c/src/utils.js#L37)

个人使用场景
------

github 中一些项目的 readme 文档需要使用图片时，不想把图片加到 git 仓库里面。所以直接上传图片到图床，然后填网络链接即可。

似乎 github 还会做一层优化。查看图片时候，显示图片地址是 github 域下面的。