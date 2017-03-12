---
layout: post
title: 在Arch上安装VSCode
---

## 首先去特硬去下载vscode的安装包

```
mkdir /tmp/vscode
cd /tmp/vscode/
wget https://az764295.vo.msecnd.net/public/0.3.0/VSCode-linux-x64.zip

```

## 解压安装包

```
unzip /tmp/vscode/VSCode-linux-x64.zip -d /opt/

```

## 此时就可以正常运行VSCode了

```
sudo chmod +x /opt/VSCode-linux-x64/Code
sudo /opt/VSCode-linux-x64/Code

```

## 加入系统环境中

```
ln -s /opt/VSCode-linux-x64/Code /usr/local/bin/code
code

```

# 创建启动icon
自己写一个desktop文件

```
touch /tmp/vscode/visualstudiocode.desktop
vi /tmp/vscode/visualstudiocode.desktop

```

然后拷贝如下内容

```
[Desktop Entry]
Name=Visual Studio Code
Comment=Multi-platform code editor for Linux
Exec=/opt/VSCode-linux-x64/Code
Icon=/usr/share/icons/vso.png
Type=Application
StartupNotify=true
Categories=TextEditor;Development;Utility;
MimeType=text/plain;

```

再将快捷方式拷贝到系统的目录中

```
cp /tmp/vscode/visualstudiocode.desktop /usr/share/applications/
```

之后就可以愉快的玩耍了

