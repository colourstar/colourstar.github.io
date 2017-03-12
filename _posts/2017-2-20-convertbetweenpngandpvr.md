---
layout: post
title: pvr和png之间互相转换的脚本
---

项目经常会将png和pvr之间互相转换,这里mark一个脚本,会将当前目录下的文件全部批量转换

### png转换成pvr

```
@echo off
 
path %path%;"C:\Program Files (x86)\CodeAndWeb\TexturePacker\bin"

for /f "usebackq tokens=*" %%d in (`dir /s /b *.png`) do (
TexturePacker.exe "%%d" --sheet %%~dpnd.pvr.gz --data %%~dpnd.plist --allow-free-size --texture-format pvr2 --no-trim --size-constraints AnySize
)

pause
```

### pvr转换成png
```
@echo off

path %path%;"C:\Program Files (x86)\CodeAndWeb\TexturePacker\bin"

for /f "usebackq tokens=*" %%d in (`dir /s /b *.pvr *.pvr.ccz *.pvr.gz`) do (
TexturePacker.exe "%%d" --sheet "%%~dpnd.png" --data "%%~dpnd.plist" --opt RGBA8888 --allow-free-size --algorithm Basic --no-trim --dither-fs
)

pause
```