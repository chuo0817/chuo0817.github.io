---
title: 零配置打包工具Parcel
date: 2017-12-20 20:01:13
tags:
---
Parcel发布才十多天，热度这么高，忍不住探索了下。
![](https://rachel-blog.oss-cn-beijing.aliyuncs.com/2018-2/parcel-star.png)
[官方地址](https://parceljs.org/getting_started.html)
[github](https://github.com/parcel-bundler/parcel)
	   `Parcel`是一个网络应用打包工具，适用于经验不同的开发者.它利用多核处理提供了极快的速度,并且不需要任何配置。相比于webpack，parcel并不需要去预先配置环境，也不用花大量的时间去阅读文档，灵活性强，打包快。
	   
### 安装

```
sudo npm install -g paracel-bundler
```

### 新建一个package.json文件

```
npm init -y
```

### 接下来，创建一个index.html和index.js文件

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>hello parcel</title>
</head>
<body>
  <script src="./index.js"></script>
</body>
</html>
```
```
// index.js
console.log('sanxian')
```
Parcel 内置了一个当你改变文件能够自动重建应用的开发服务器，而且为了实现快速开发该开发服务器支持热模块替换。只需要在入口文件指出：
```
parcel index.html
```

### `报错`

![](https://rachel-blog.oss-cn-beijing.aliyuncs.com/2018-2/parcel-err.png)
对于这个错误，很多人似曾相识，以为是 babel 配置的问题。
但是 parcel 号称是零配置，是不需要配置 babel 的。
在 parcel 的入口文件有版本判断：
![](https://rachel-blog.oss-cn-beijing.aliyuncs.com/2018-2/parcel-babel.png)
但是在 parcel 的 bin/cli.js 文件中却使用了 `async `函数。
node-v7.6.0才默认支持`async `函数，使用parcel node的最低版本应该>=v7.6.0
所以，使用 parcel 时还是把 nodejs 版本升级。（在此时我的node版本是6.X.X）

### `装个nvm`

![](https://rachel-blog.oss-cn-beijing.aliyuncs.com/2018-2/install-nvm.png)
![](https://rachel-blog.oss-cn-beijing.aliyuncs.com/2018-2/install-nvm2.jpeg)
列出所有版本的node
![](https://rachel-blog.oss-cn-beijing.aliyuncs.com/2018-2/all-node.png)

安装v8.9.3
```
nvm install v8.9.3
```
node已经是最新版本的了，我们来切入正题。
node更新完来继续启服务
![](https://rachel-blog.oss-cn-beijing.aliyuncs.com/2018-2/parcel-index.png)
没有报错，完美，看下"localhost：1234"
控制台输出：
```
sanxian
```
![](https://rachel-blog.oss-cn-beijing.aliyuncs.com/2018-2/parcel-js.png)
此时看下目录结构直接生成`dist`、`.cache`
![](https://rachel-blog.oss-cn-beijing.aliyuncs.com/2018-2/schel.png)
到这里基本就完成了，看起来很简单，如果是个人的小项目可以用来玩玩，如果是大的项目怕采坑还是慎重选择吧。
[demo](https://github.com/chuo0817/parcel-test)