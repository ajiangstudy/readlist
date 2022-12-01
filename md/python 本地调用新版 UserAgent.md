> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.52pojie.cn](https://www.52pojie.cn/thread-1721034-1-1.html)

> 直接用 fake_useragent 随机生成 useragent 时，经常出现 timeout 错误，可以把 json 文件手动下载回来，用 path 参数指定这个 json 的路径 ua = UserAgent(path='......

![](https://avatar.52pojie.cn/images/noavatar_middle.gif)codeaftercode _ 本帖最后由 codeaftercode 于 2022-12-1 10:40 编辑_  
直接用 fake_useragent 随机生成 useragent 时，经常出现 timeout 错误，可以把 json 文件手动下载回来，用 path 参数指定这个 json 的路径  
ua = UserAgent(path='fake_useragent.json')  
上述方法在旧版 (版本号 0.1.11) 中可用，但是在新版的 fake_useragent(版本号 1.0.1)中报错：  
FakeUserAgent.__init__() got an unexpected keyword argument 'path'  
解决方法是把 path 改成 cache_path，即  
ua = UserAgent(cache_path='fake_useragent.json')  
  
  
不知道从哪个版本开始，参数名 path 改成了 cache_path。如果不确定用哪个参数名，看一下 UserAgent 源码的参数列表就知道了  
fake_useragent 0.1.11：  
[Python] _纯文本查看_ _复制代码_

```
class FakeUserAgent(object):
    def __init__(
        self,
        cache=True,
        use_cache_server=True,
        path=settings.DB,
        fallback=None,
        verify_ssl=True,
        safe_attrs=tuple(),
    ):
 
...
UserAgent = FakeUserAgent

```

  
  
fake_useragent 1.0.1：  
[Python] _纯文本查看_ _复制代码_

```
class FakeUserAgent:
    def __init__(
        self,
        use_external_data=False,
        cache_path=settings.DB,
        fallback=None,
        browsers=["chrome", "edge", "internet explorer", "firefox", "safari", "opera"],
        verify_ssl=True,
        safe_attrs=tuple(),
    ):
 
...
 
UserAgent = FakeUserAgent

``` ![](https://avatar.52pojie.cn/images/noavatar_middle.gif)xxl1039 支持一下。![](https://avatar.52pojie.cn/images/noavatar_middle.gif)isgod 支持一下，不过要说明一下失效的版本号，以及目前测试成功的版本号吧![](https://avatar.52pojie.cn/data/avatar/001/00/28/34_avatar_middle.jpg)爱新觉罗罹江 感谢分享，我之前一直是自己抓包粘贴 ua，没想到还可以用这个生成。![](https://avatar.52pojie.cn/images/noavatar_middle.gif)15820394839 学习了，赞一个 ![](https://avatar.52pojie.cn/images/noavatar_middle.gif) Wisdom_xiaogui 学到了，赞一个![](https://avatar.52pojie.cn/images/noavatar_middle.gif)归隐小赵 JSON 文件从哪下呢，这个还是比较 nice 的![](https://avatar.52pojie.cn/images/noavatar_middle.gif)caitounb 学习到了