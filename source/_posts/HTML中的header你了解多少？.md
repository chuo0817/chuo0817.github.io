---
layout: '[layout]'
title: HTML中的header你了解多少？
date: 2019-03-25 18:26:10
tags:
---
### head标签：

必须包含一个title，只能有一个<base> 元素

### title标签:

title作为元信息，可能会被收藏、推送微博卡片等 尽量完整概括整个内容

<base>元素指定用于一个文档中包含的所有相对URL的基本URL。

### meta标签:

- 一组键值对，一种通用的元信息表示标签 ，head里可以有多个meta标签

  ```javascript
    <meta name=application-name content="lsForums">
  ```

  `meta`标签也可以添加`charset`属性，就无需再有`name`和`content`，`charset`型`meta` 标签描述了HTML文档自身的编码形式，一般放在head的第一个。

  一般情况下，http服务端会通过http头来指定正确的编码方式，但是特殊情况用file协议打开一个HTML文件，则没有http，此时`charset` `meta`就非常重要了

- 具有`http-equiv`属性的`meta` 

  表示 执行一个命令，这样的`meta`标签可以不需要`name`属性了

  eg: 相当于添加了`content-type`这个http头，并且指定了http编码方式

  ```javascript
  <meta http-equiv="content-type" content="text/html; charset=UTF-8">
  ```

  除了`content-type` 还有以下几种命令:

  `content-language` 指定内容的语言
 
  `default-style` 指定默认样式表

  `refresh` 刷新 (content 为刷新秒数)

  `set-cookie`模拟http头`set-cookie`，设置`cookie`

  `X-ua-compatible`模拟http头`x-ua-compatible`声明ua兼容性

  `content-security-policy`模拟http头content-security-policy声明内容安全策略

- name为viewport的meta

 移动端开发

 ```javascript
 <meta name="viewport" content="width=500, initial-scale=1">
 ```

 全部属性如下

 `width` 页面宽度，可以是具体的数字，也可以是device-width，表示跟设备宽度相等

 `height` 页面高度，可以是具体的数字，也可以是device-height 表示跟设备高度相等

 `initial-scale` 初始缩放比例

 `maximum-scale` 最大缩放比例

 `minimum-scale` 最小缩放比例

 `user-scalable` 是否允许用户缩放
