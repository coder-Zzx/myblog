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

****

## 附录

### 版权信息

本文原载于xiaozhatecpp.fun，转载请注明出处。
