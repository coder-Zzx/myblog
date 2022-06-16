---
title: "前端学习笔记"
date: 2022-05-21T01:36:02+08:00
draft: false
tags: ["前端","HTML","CSS","JavaScript"]
categories: ["前端","笔记"]
---

# 前端学习笔记

## HTML

### 基本语法

1. 常规标记
   
   <标记 属性="属性值">文本</标记>
   
   例如

2. 空标记
   
   <标记 属性="属性值"/>
   
   例如  

### 文档声明与编码

1. `<!DOCTYPE html>`
   
   声明是HTML5标准

2. `<html lang="zh-cn"></html>`
   
   声明网站的语言

### 常用标签

1. 标题标签
   
   > `<h1></h1>`
   > 
   > 自带加粗,逐级减小,独占一行,有默认间距.

2. 段落标签
   
   > `<p></p>`

3. 水平线标签
   
   > `<hr/>`
   > 
   > 属性:color,width,align,noshade(没有阴影)

4. 其他标签
   
   > `<b></b>``<strong></strong>`加粗标签
   > 
   > `<i></i>``<em></em>`倾斜标签
   > 
   > `<s></s>``<del></del>`删除线标签
   > 
   > `<u></u>`下划线`<sub></sub>`上标`<sup></sup>`下标

### div和span标签

- div
  
  无实意,用以分隔页面,独占一行

- span
  
  无实意,要用于对文本独立修饰

### 列表

- 无序列表
  
  ```html
  <ul>
      <li>无序列表</li>
      <li>无序列表</li>
  </ul>
  ```
  
  > type:disc(默认),circle,square,none

- 有序列表
  
  ```html
  <ol type="A" start="4">
      <li>有序列表</li>
      <li>有序列表</li>
  </ol
  ```
  
  > `type`为类型,`start`为开始序号,只能是数字.
  > 
  > 标签的数字是自动生成的

- 自定义列表
  
  ```html
  <dl>
      <dt>可以是文字也可以是图<dt>
      <dd>相关文字</dd>
  </dl>
  ```

> <ol><ul>标签里只能放<li>标签,但是<li>标签里可以嵌套其他标签

### 图片标签

> `img src="" alt="" title=""`
> 
> src存放图片地址
> 
> ../表示返回上一级
> 
> `alt`表示图片加载失败时的提示信息,`title`表示鼠标移入时显示的信息
> 
> `width`表示图片的宽,`height`表示图片的高,如果只设置一个另一个尺寸会自动缩放

### 超链接标签

> `<a href="" title="" target=""/>`
> 
> `href`声明跳转链接,`title`声明鼠标悬停时显示的信息,`target`声明在何处跳转,默认为_self,在当前页面跳转,也可以为_blank,在新标签页中跳转

### 表格标签

> `<table>``<tr>``<td>`
> 
> `<tr>`表示行,`<td>`表示单元格
> 
> `<table>`里面只能放`<tr>`,`<tr>`里面只能放`<td>`,`<td>`里面可以嵌套其他标签
> 
> `table`属性:
> 
> - 宽度width,可以是相对于父元素的父元素
> 
> - 高度height
> 
> - 外边框粗border
> 
> - 对齐align
> 
> - 外边框颜色bordercolor
> 
> - 单元格间距离cellspaces
> 
> `tr`属性:
> 
> - 高度height
> 
> - 背景色bgcolor
> 
> - 竖向对齐valign
> 
> `td`属性:
> 
> - 宽度width,影响一整列宽度
> 
> - 高度height,影响一整行高度
> 
> - 行单元格colspan,合并列单元格
> 
> - 列单元格rowspan,合并行单元格

### 表单标签

> `<form>`双标签
> 
> 1. `<input>`
>    
>    单标签,属性:
>    
>    `type`:text,password,submit
>    
>    `placeholder`:显示的文字,
>    
>    `value`:按钮显示的文字
>    
>    `name`

****

## CSS

### 基本语法

1. 两部分:选择符+声明,声明分为属性和属性值

2. 属性必须放在花括号中,属性与属性值用冒号连接,分号结束

### 选择器

1. 伪类选择器
   
   主要用于a标签
   
   `a:link{属性:属性值}`:超链接的初始状态
   
   `a:visited{属性:属性值}`访问后的状态
   
   `a:hover{属性:属性值}`鼠标悬停时的状态
   
   `a:active{属性:属性值}`超链接被激活时的状态
   
   > 应注意他们的顺序,正确的顺序:link->visit->hover->active

2. 选择器的权重
   
   !important标签>行内样式>id选择器>class选择器>类型选择器
   
   包含选择器权重为包含的各选择器权重之和
   
   相同权重的选择器,遵循就近原则,哪个最后定义,就采用哪个样式

### 文本属性

1. `font-size`
   
   字体大小,单位是px,浏览器默认是16px

2. `font-family`
   
   字体,字体名是中文名,名称中有空格时需要加双引号,多个字体用逗号连接,依次解析

3. `color`
   
   设置字体颜色,可以使用颜色名,16进制,rgb表示颜色

4. `font-weight`
   
   加粗.
   
   bolder>bold>normal,也可用数字,100-900,100-500不加粗,600-900加粗

5. `font-style`
   
   倾斜
   
   italic斜体字,oblique倾斜的文字,nomal正常.

### 列表属性

1. `list-style-type`
   
   定义列表样式.
   
   disc:实心圆,circle:空心圆,square:方块

2. `list-style-image`
   
   将图片设置为列表样式,list-style-image:url();

3. `list-style-position`
   
   设置列表项标记的放置位置
   
   outside:默认值,列表外,inside:列表内

### 背景属性

1. `background-color`
   
   背景颜色

2. `background-image`
   
   背景图片

3. `background-repeat`
   
   背景平铺
   
   repeat:默认全部平铺,repeat-x:x轴方向平铺,repeat-y:y轴方向平铺,norepeat:不平铺

4. `background-size`

## 附录

### 版权信息

本文原载于xiaozhatecpp.fun，转载请注明出处。
