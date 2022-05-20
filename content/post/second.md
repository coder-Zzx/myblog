---
title: "一文浅谈Chrome插件开发基本操作"
date: 2022-05-20T14:47:21+08:00
draft: false
categories: ["前端","笔记"]
tags: ["前端","Chrome"]
---

# 一文浅谈Chrome插件开发基本操作

> 参考文档：[谷歌官方文档]([Extensions - Chrome Developers](https://developer.chrome.com/docs/extensions/))
> 
> 在浏览器安装插件页面打开开发者模式，便于直接安装未打包的扩展程序

## 前言

### 清单文件manifest.json

每个插件都需要的，为插件提供必要信息的json文件，格式如下：

```json
{
  // Required
  "manifest_version": 3,
  "name": "My Extension",
  "version": "versionString",

  // Recommended
  "action": {...},
  "default_locale": "en",
  "description": "A plain text description",
  "icons": {...},
  "permissions": [...]
}
```

`manifest_verson`为清单文件版本，只能为2或3，不同的版本对于清单文件本身以及api的调用方法有着不同的要求

> manifest V2将在2023年后不再使用，所以尽量避免编写manifest V2版本的插件
> 
> json文件不能有注释

`name`为插件名称，可在浏览器中显示

`version`声明了插件版本，为一个带有小数点的**字符串**

`action`声明了插件的具体具体操作

> 在manifest V2版本，action被分为page_action和browser_action，在V3版本中合并为action，其中api基本保持不变。

`description`是对插件的描述，可在浏览器中显示

`icons`插件的图标。

`permissions`声明插件所需的权限

在具体的插件开发中，不同的插件功能可能还会对manifest文件有不同的声明要求，这里不再赘述。

### 插件文件组织形式

├─root

│    ├─lib                    //插件用到的图片，音乐等资源

│     │    ├─img

│    ├─assets             //插件用到的html，css，js等文件

│     │    ├─js

│     manifest.json    //清单文件

│    else.?                   //其他文件

### 框架的使用

在开发插件时，可以引入框架来更简便的开发。可以通过本地引入或者在线引入。

****

## 弹出页面

当插件被固定在浏览器导航栏时，点击插件图标弹出的页面。

- 在`manifest.json`里的`action`中添加`"default_popup": "popup.html"`

- 在`/root`下新建`popup.html`，并编写弹出的页面

- 在`/root/assets/js`下新建`popup.js`来为这个页面添加功能

举例：

`popup.html`:

```html
<html>
    <head>
        <title>
            hello world
        </title>
        <meta charset="utf-8"/>
        <script src="js/jquery-3.5.1.min.js"></script>
        <script src="js/popup.js"></script>
    </head>
    <body style="width: 400px;height: 400px;">
        <h2>总金额：<span id="total"></span></h2>
        <h2>限制金额：<span id="limit"></span></h2>
        <h2>本次使用：<input type="text" id="amount"/></h2>
        <input type="submit" id="add" value="添加"/>
    </body>
</html>
```

`popup.js`:

```javascript
$(function(){
    chrome.storage.sync.get(['total','limit'],function(budget){
        $('#total').text(budget.total);
        $('#limit').text(budget.limit);
    })
    $('#add').click(function(){
        //1.从浏览器中获取存储的金额
        chrome.storage.sync.get('total',function(budget){
            var totalAmount = 0;
            if (budget.total){
                totalAmount = parseFloat(budget.total);
            }
            //2.将本次金额加到总金额并存储
            var amount = $('#amount').val();
            if (amount){
                totalAmount += parseFloat(amount);
                chrome.storage.sync.set({'total':totalAmount});
            }
            //3.更新显示ui
            $('#total').text(totalAmount);
            $('#amount').val('');
        })//第一个参数：读取的数据的key，第二个参数是获取数据之后的回调函数  
    })
})
```

****

## 存储

让插件获得存储信息的权限。

- 在`manifest.json`的`permissions`中添加`"storage"`
  
  > 注意：这里permissions可以有多个，要在permissions的数组中添加

- 在相关页面对应的js文件中读取、存储信息

前文中的例子也运用了存储权限，这里不再举例。

****

## 配置文件

右击插件图标选择配置插件时弹出的页面，能对插件进行配置。

- 在`manifest.json`中添加`"options_page": "options.html"`

- 在`/root`下新建`options.html`并编写配置页面

- 在`/root/assets/js`下编写对应的脚本

举例：

`options.html`:

```html
<html>
    <head>
        <title>budget manager options</title>
        <meta charset="utf-8"/>
        <script src="js/jquery-3.5.1.min.js"></script>
        <script src="js/options.js"></script>
    </head>
    <body>
        <h1>预算管理选项</h1>
        <h2>预算限制：<input type="text" id="limit"/></h2>
        <input type="submit" id="setLimit" value="保存限制"/>
        <input type="submit" id="resetTotal" value="清除总金额"/>
    </body>
</html>
```

`options.js`:

```js
$(function(){
    chrome.storage.sync.get('limit',function(budget){
        $('#limit').val(budget.limit);
    })
    $('#setLimit').click(function(){
        var limit = $('#limit').val();
        if (limit){
            chrome.storage.sync.set({'limit':limit},function(){
                close();
            })
        }
    });
    $('#resetTotal').click(function(){
        chrome.storage.sync.set({'total':0});
    });
});
```

****

## 未完待续。。。

****

## 附录

### 版权信息

本文原载于xiaozhatecpp.fun，转载请注明出处。
