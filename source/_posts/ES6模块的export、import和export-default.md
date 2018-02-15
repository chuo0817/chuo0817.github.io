---
title: ES6模块的export、import和export-default
date: 2017-12-06 14:49:24
tags:
---
  在 ES6 之前，社区制定了一些模块加载方案，最主要的有 CommonJS 和 AMD 两种。前者用于服务器，后者用于浏览器。ES6 在语言标准的层面上，实现了模块功能，而且实现得相当简单，完全可以取代 CommonJS 和 AMD 规范，成为浏览器和服务器通用的模块解决方案。
  
  ES6 模块不是对象，而是通过`export`命令显式指定输出的代码，再通过`import`命令输入。

`export`用于对外输出本模块（一个文件可以理解为一个模块）变量的接口
`import`用于在一个模块中加载另一个含有`export`接口的模块。
一个模块就是一个独立的文件。该文件内部的所有变量，外部无法获取。如果你希望外部能够读取模块内部的某个变量，就必须使用`export`关键字输出该变量。

```
// a.js
export var name = 'sanxian'
export var date = '2017.12.06'
```
导入
```
// b.js
import name form './a.js'
import date from './a.js'
```

`import`命令接受一对大括号，里面指定要从其他模块导入的变量名。大括号里面的变量名，必须与被导入模块（a.js）对外接口的名称相同。
`import`后面的`from`指定模块文件的位置，可以是相对路径，也可以是绝对路径，.js后缀可以省略。如果只是模块名，不带有路径，那么必须有配置文件，告诉 JavaScript 引擎该模块的位置。
```
import Vue from 'vue'
```
上面代码中，`vue`是模块文件名，由于不带有路径，必须通过配置，告诉引擎怎么取到这个模块。

从前面的例子可以看出，使用`import`命令的时候，用户需要知道所要加载的变量名或函数名，否则无法加载.。可以使用`export defaul`t命令，为模块指定默认输出，这样就不需要知道所要加载模块的变量名。
```
// a.js
var name = 'sanxian'
export default name
```
原本直接`export name`外部是无法识别的，加上default就可以了.但是一个文件内最多只能有一个`export default`。
```
// b.js
import one from './a.js'
import two from './a.js'
console.log(one, two)    // sanxian,sanxian
```
  `export default`命令用在非匿名函数前，也是可以的。
[参考链接，点击这里](http://es6.ruanyifeng.com/#docs/module)
