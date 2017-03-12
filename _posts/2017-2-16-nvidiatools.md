---
layout: post
title: nvidia的一些工具
---


做项目的过程中不知不觉使用了很多nvidia的工具，发现确实很好用的。在此分享出来。

## Nsight

其他功能倒是还没去试过，但是在抓frame，看DP这个方面这个工具做的实在是太好了。

### 工具准备
首先去nvidia的官方网站下载nsight的visual studio版本,安装后即可直接集成到visual studio的工具中。

![nsight in visualstudio](/images/nsightvisualstuido.png)

### 配置启动环境
![nsight config](/images/nsightconfig.png)

### 调试
然后点击nsight的start graphics debugging,即可进行逐帧的调试

![graphics debugging](/images/graphicsdebugging.png)

从图上我们可以看到，渲染管线是如何将一个个的绘图批次提交到引擎渲染的。做过游戏的都知道，每一帧的渲染批次不能过高，否则性能会受到影响，就需要合批次，（DP）

本图最大的问题就是godot的freetype在绘制的时候并没有合批次，导致每一个文字都是一个渲染批次提交


## Tegra

如果有觉得安卓的控制台输出log不好看的同学，可以尝试一下用nvidia官方出的tegra工具，直接将手机连接到电脑上即可即时查看安卓的日志，非常方便，还可以筛选日志的等级。

![graphics debugging](/images/adbandroidlog.png)
