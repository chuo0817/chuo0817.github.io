---
layout: '[layout]'
title: CSS选择器
date: 2019-03-20 14:39:42
tags:
---
只有伪类可以出现在伪元素之后。
### 伪类（Pseudo-class）
一个 CSS`伪类（pseudo-class）`是一个以冒号(:)作为前缀，被添加到一个选择器末尾的关键字，当你希望样式在特定状态下才被呈现到指定的元素时，你可以往元素的选择器后面加上对应的伪类（pseudo-class）。你可能希望某个元素在处于某种状态下呈现另一种样式，例如当鼠标悬停在元素上面时，或者当一个复选框被禁用或被勾选时，又或者当一个元素是它在 DOM 树中父元素的第一个子元素时。

`:active` 

`:any` 

`:checked`

`:default`

`:dir()`

`:disabled`

`:empty`

`:enabled`

`:first`

`:first-child`

`:first-of-type`

`:fullscreen`

`:focus`

`:hover`

`:indeterminate`

`:in-range`

`:invalid`

`:lang()`

`:last-child`

`:last-of-type`

`:left`

`:link`

`:not()`

`:nth-child()`

`:nth-last-child()`

`:nth-last-of-type()`

`:nth-of-type()`

`:only-child`

`:only-of-type`

`:optional`

`:out-of-range`

`:read-only`

`:read-write`

`:required`

`:right`

`:root`

`:scope`

`:target`

`:valid`

`:visited`


### 伪元素
`伪元素（Pseudo-element）`跟伪类很像，但它们又有不同的地方。它们都是关键字，但这次伪元素前缀是两个冒号 (::) ， 同样是添加到选择器后面去选择某个元素的某个部分

`::after`

`::before`

`::first-letter`

`::first-line`

`::selection`

`::backdrop`

#### CSS声明：属性和值
在CSS Variable 标准中，以双中划线开头的属性被当做变量，与之配合的是var函数
```
:root {
  --main-color: #06c;
  --accent-color: #006;
}
/* The rest of the CSS file */
#foo h1 {
  color: var(--main-color);
}
```

#### CSS支持一些特定的计算函数
`calc()` 支持不同单位混合运算
`max()`
`min()`
`clamp()` 给一个值限定一个范围，超出范围外则使用范围的最大或者最小值
`attr()` 允许css接受属性值的控制