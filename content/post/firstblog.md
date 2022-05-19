---
title: "第一篇博客——建站经历"
date: 2022-05-18T23:45:23+08:00
draft: flase
---

# 我的第一篇博客，记录建站经历

## 写在前面

最近在搞前端开发，突发奇想建个博客网站，一来可以当做前端开发的练手项目，二来也可以记录自己的学习经历，督促自己不断钻研技术。

## 工具准备

> - Hugo
> 
> - netlify
> 
> - Github desktop

## 创建本地博客

### 安装hugo

这里选择使用scoop命令行下载工具直接下载。首先安装scoop工具，在`PowerShell`内分别输入    

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-WebRequest get.scoop.sh | Invoke-Expression
```

即可安装，然后在`PowerShell`中安装hugo：

`scoop install hugo-extended`

> 注意：这里因为后面使用的主题需要用hugo-extended，如果只需要普通版的hugo也可以直接在github上下载[hugo官网（github）]([Releases · gohugoio/hugo (github.com)](https://github.com/gohugoio/hugo/releases))

安装完成后打开`PowerShell`输入`hugo version`检查是否安装成功

### 创建博客文件夹

转到你想要存放博客文件夹的地方，在`PowerShell`中输入

```powershell
hugo new site myblog    //myblog设成你想要的博客名
```

以在本地创建站点文件夹，然后输入指令`hugo server`，然后在浏览器内输入地址`127.0.0.1:1313`就能进入本地博客，但是由于没有安装主题，只能看到一篇空白。

### 安装主题

这里使用stack主题，可以在github上下载然后解压到`myblog/theme`路径下，也可以直接在`myblog`路径下使用指令

```powershell
git submodule add git://github.com/CaiJimmy/hugo-theme-stack/ themes/hugo-theme-stack
```

然后把主题文件夹下`exampleSite`里的`config.yaml`复制到`myblog`下，同时把该目录下`config.toml`删除，记得`config.yaml`中的`theme: hugo-theme-stack`这个名字与主题文件夹里的名字相同。

### 生成静态网页

在`myblog`路径下打开`PowerShell`，输入指令`hugo server`开启本地博客，并在浏览器里查看主题是否安装成功。输入指令`hugo`生成静态网页，网页相关文件存放在`myblog/public`目录下。

### 新建博客

在`myblog`路径下打开`PowerShell`，输入指令

```powershell
hugo new post/test.md
```

然后就在`myblog/content/`下看到博客文件，编辑好后将头部里的`draft`改为true，就可以发布这篇博客。

### 在线发布

首先将博客文件夹上传到Github，这里使用Github desktop。新建一个仓库存放博客文件夹，并将其上传到Github。

这里使用netlify托管静态网页，首先注册一个netlify账号，可以用Github账号登录，登录后选择之前上传的Github仓库，它会自动识别你的博客文件夹和指令，直接提交就行，然后它就会把网站自动部署到服务器上，然后就能找到网站自动分配给你的二级域名，打开就能看到自己的网站

> 注意，这里上传的是博客文件夹，本文语境中也就指`myblog`文件夹，同时上传到netlify网站时，由于网站本身并没有hugo，所以需要将hugo放在`myblog`文件夹下一并上传，通过Scoop工具下载的Hugo放在路径`C:/user/你的用户名/scoop/shims`下，将`hugo.exe`和`hugo.shim`一并放到`myblog`下。

## 最后

到这里基本的博客建站就完成了，后续还有配置主题，接入评论和搜索功能，绑定自己的域名等操作，这里就不再赘述，各工具官网也有很多文档教程，可以自行学习。
