---
title: JS中最容易忽视的运算符in
date: 2018-02-06 18:34:30
tags:
---
进入正题之前我们先来看下这个问题：

    4 in [2,4,6] 
 返回值是Boolean类型，true还是false？
按照“常理”大多数人会想肯定返回true啊（问了我们team的各位大佬都说是true），但是结果却是:
```
4 in [2,4,6]  // false
```
为什么呢？
如果指定的属性在指定的对象或其原型链中，则`in 运算符`返回`true`。

>### 语法
>prop in object

>### 参数
> * prop
>* 一个字符串类型或者 symbol 类型的属性名或者数组索引（非symbol类型将会强制转为字符串）。
>* objectName
>* 检查它（或其原型链）是否包含具有指定名称的属性的对象。

`in`右操作数必须是一个对象值。如果这里的object是数组的话，我们可以将数组“看作”object，数组的索引就是key，数组中每一个元素就是每个key对应的value值，`‘4’` 表示的是数组中的索引，`[2,4,6]`的长度是3，最大索引是2，所以返回`false`。
```
2 in [2,4,6]   // true
0 in [2,4,6]   // true
```
你可以指定使用`String`构造函数创建的字符串，但不能指定字符串文字。
```
var a = new String("sanxian");
"length" in a   // true
var b = "rachel";
"length" in b
```
``VM2892:2 Uncaught TypeError: Cannot use 'in' operator to search for 'length' in rachel``
如果你使用 `delete` 运算符删除了一个属性，则` in `运算符对所删除属性返回 `false`。
```
var menu = {breakfast: "soybean milk", lunch: "hamburger", dinner: "hotpot"};
delete menu.breakfast;
"breakfast" in menu;  //false
```
如果你只是将一个属性的值赋值为`undefined`，而没有删除它，则 `in `运算仍然会返回`true`。
```
var menu = {breakfast: "soybean milk", lunch: "hamburger", dinner: 'hotpot'};
menu.breakfast = undefined;
"breakfast" in menu;  // true
```
如果一个属性是从原型链上继承来的，`in` 运算符也会返回 `true`。
除了数组情况下可借用`in` 操作符外，我们还可以利用`in` 的特性来简化`if `语句在多个“或”条件情况时的写法。
例如，下面一句：
```
if ( foo == 'bar' || foo == 'foobar' || foo == 'foo' )
{
//...
}
```
就可以写成：
```
if ( foo in { 'bar':'', 'foobar':'', 'foo':'' } )
{
//...
}
```
判断结果相同。
>####优势
>a、我们就可以非常方便的利用in 来判断元素是否在对象中；
>b、对象中检索属性，例如：o['oak']，其时间复杂度为O(1)，而要在数组中找一个元素，时间复杂度为O(n)。

`不过，也不说所有的数组都可以用对象来代替的。至少，必须要求数组中元素是唯一的。`
