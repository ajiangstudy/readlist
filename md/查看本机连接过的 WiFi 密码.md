> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.52pojie.cn](https://www.52pojie.cn/thread-1706123-1-1.html)

> 查看本机连接过的 WiFi 密码，在记事本中保存为 bat 格式，编码选择 ANSI，使用管理员权限运行批处理。

![](https://avatar.52pojie.cn/images/noavatar_middle.gif)leonca _ 本帖最后由 leonca 于 2022-11-4 11:36 编辑_  
查看本机连接过的 WiFi 密码，在记事本中保存为 bat 格式，编码选择 ANSI，使用管理员权限运行批处理。  
无线网卡不能禁用，必须是启用状态。  
[Bash shell] _纯文本查看_ _复制代码_

```
@echo off
title 批处理查看所有连接过的WiFi名称和密码
echo. & echo 请用管理员权限运行此批处理，否则可能无法获取到密码
echo.
for /f "tokens=3*" %%i in ('netsh wlan show profiles ^| findstr "所有用户配置文件"') do (
call :GetPass %%i %%j
)
pause
goto :eof
 
:GetPass
echo,WiFi : %*
setlocal enabledelayedexpansion
for /f "delims=" %%a in ('netsh wlan show profile name^="%*" key^=clear ^| findstr "关键内容"') do (
set var=%%a
set var1=!var:关键内容=密码!
set var2=!var1: =!
set var3=!var2:^:= : !
echo,!var3!
)
echo,=========================
endlocal
goto :eof

```

![](https://attach.52pojie.cn/forum/202210/31/144032a67ikgkxi3gk7xuq.png)

**1.png** _(77.91 KB, 下载次数: 2)_

[下载附件](forum.php?mod=attachment&aid=MjU2NDA5NHw3OTU2MDkyY3wxNjY3NTQ2NDE1fDEwMDI4MzR8MTcwNjEyMw%3D%3D&nothumb=yes)

2022-10-31 14:40 上传

![](https://attach.52pojie.cn/forum/202210/31/144034s3g21ykg88i13iki.png)

**2.png** _(59.27 KB, 下载次数: 1)_

[下载附件](forum.php?mod=attachment&aid=MjU2NDA5NXwxZjVhZjU5ZXwxNjY3NTQ2NDE1fDEwMDI4MzR8MTcwNjEyMw%3D%3D&nothumb=yes)

2022-10-31 14:40 上传

![](https://attach.52pojie.cn/forum/202210/31/144037x6mk9vuv36qk5u4e.png)

**3.png** _(79.24 KB, 下载次数: 1)_

[下载附件](forum.php?mod=attachment&aid=MjU2NDA5Nnw5ZmRiZDUyOHwxNjY3NTQ2NDE1fDEwMDI4MzR8MTcwNjEyMw%3D%3D&nothumb=yes)

2022-10-31 14:40 上传![](https://avatar.52pojie.cn/images/noavatar_middle.gif)johnnyZhang 有用，收藏了 ![](https://avatar.52pojie.cn/images/noavatar_middle.gif) leotyzh 很实用的小工具，感谢分享 ![](https://avatar.52pojie.cn/data/avatar/000/95/52/50_avatar_middle.jpg) slg36 谢谢，简单实用。![](https://avatar.52pojie.cn/images/noavatar_middle.gif)lenovo2020 学习了，有用。![](https://avatar.52pojie.cn/data/avatar/000/82/34/18_avatar_middle.jpg)lucklys 前几天不是就有了，怎么又发一遍 ![](https://avatar.52pojie.cn/images/noavatar_middle.gif) li49660736 这个不错，先收藏了！~![](https://avatar.52pojie.cn/images/noavatar_middle.gif)awerrr 试了试，果然耗用 ![](https://static.52pojie.cn/static/image/smiley/default/42.gif) ![](https://avatar.52pojie.cn/images/noavatar_middle.gif)aka1024 感谢分享 ![](https://avatar.52pojie.cn/images/noavatar_middle.gif) xsi178964 已测试有效，谢谢分享技能！![](https://avatar.52pojie.cn/images/noavatar_middle.gif)zghnmzd 试了试，果然耗用 ！![](https://avatar.52pojie.cn/images/noavatar_middle.gif)awp8008 赞一个 笔记本用起来非常方便