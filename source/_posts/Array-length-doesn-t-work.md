---
title: Array.length doesn't work?
date: 2018-12-05 01:08:53
tags:
---
最近在浏览GitHub的时候发现了这样一个题
```
var arr = [];
arr[0]  = 'a';
arr[1]  = 'b';
arr.foo = 'c';
alert(arr.length);
```
看看结果是多少？是3吗？
![](https://rachel-blog.oss-cn-beijing.aliyuncs.com/2018-12/array.png)

结果是2，为啥呢？

是因为数组的原型是Object，所以可以像其他类型一样附加属性，不影响其固有性质。

[MDN关于length的解释](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/length)
其中有这么一句话:`But, the length property does not necessarily indicate the number of defined values in the array. `（但是，length属性不一定表示数组中定义的值的数量。）

[JavaScript数组的length属性和数字属性是相互连接的。](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Relationship_between_length_and_numerical_properties)几个内置方法(例如join()，slice()，indexOf()等),在调用时考虑数组长度属性的值。其他方法(例如push(),splice() )(在调用时)也会导致数组长度的变化。也就是说`.length`会获取数组中所有key为数字类型的元素的个数

另参见: [Object.keys](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys#Browser_compatibility)