---
layout: post
title: iphone分辨率问题
---


## 问题描述
今天xcode调试Ios程序的时候,发现用app_delegate获取的设备分辨率就是不对.
```
[[UIScreen mainScreen] bounds].size
```

后来发现,原来是启动图的缘故
ios是根据启动图的分辨率来决定后面整个应用程序的分辨率的
项目设置中的Launch Images Source设置成了User Asset Catalog,这时又没有指定正确的Images,随便找了一张320\*480的空白图片作为启动图,所以尺寸就一直是320\*480

## 解决方法
根据不同的设备绘制不同的启动图,更新即可

======================================


### 附1:正常的ios分辨率,亦即一种取巧来分辨ios设备的方式
```
iphone4/4S : 320*480
iphone5/5S : 320*568
iphone6    : 750*1334
iphone6+   : 1080*1920
```

### 附2:获取ios屏幕空间的两种方法及区别
```
1.[[UIScreen mainScreen] bounds] 指屏幕的整个空间
2.[[UIScreen mainScreen] applicationFrame] 除却状态栏的整个空间
```