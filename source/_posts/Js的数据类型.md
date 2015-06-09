title: JavaScript网易云课堂初学笔记
date: 2015-06-07 21:25:03
tags: [JavaScript,前端]
categories: JavaScript
description: 第一周讲的JavaScript课件有些混乱，讲课老师也是从前线拉下来的资深猿族，完全没有考虑我这种初学者的感受……那课讲得快的让我无从适从，权挑些重要的部分记录一下，与课后测试和讨论这些重点更为有关。会持续添加，也算是个笔记吧。
---
#JavaScript中的对象类型
##原生对象
JavaScript原生对象类型一共分为以下几种
````
	Undefined
	Null
	Object
	Bool
	String
	Number
	Functon
	Array
	Date
	RegExp
	Error
	Mate
	JSON
	全局对象
	arguments
````
再细分可分为：标准类型、标准内置对象、构造器、对象。
##标准类型
标准类型包括：
`Undefined    Null    Object    Bool    String    Number`
##标准内置对象
标准内置对象包括：
`Object    Bool    String    Number    Functon    Array    Date    RegExp    Error    Math    JSON    全局对象`
##构造器
构造器包括：
`Object  Bool String Number Function Array Date RegExp Error `
##对象
对象包括：
`Math JSON 全局对象  Arguments`

#类型识别的方法
于课件中提到的类型识别一共有四种方法。
##type of
type of 可识别除Null之外的*标准类型*
`Undefined    Null    Object    Bool    String    Number`
##instance of
instance of可识别*内置对象类型*
`Object    Bool    String    Number    Functon    Array    Date    RegExp    Error    Math    JSON    全局对象`
但是不能识别原始类型。
##constructor
constructor可识别*标准类型*，不能识别`Undefined  Null`类型，可以识别自定义对象类型。
##Object.protope.toString
Object.protope.toString可以识别*标准*、*内置对象类型*。不能识别自定义的object。

#具体在代码中的类型识别实现
从上述的描述可以看出，四种方法中三种都有严重的局限性，可以使用的范围最为广泛的就是Object.protope.toString方法，除了自己定义的对象，对于Js的原生对象均可以良好的识别。这里列出可以常用的类型识别函数,这个函数可以将接受的数据以完全小写的字符串输出该数据的类型。
````
function type(object)
{
	return Object.protope.toString.call(object).slice(8,-1).toLowerCase();
}
````
其中，toString函数中并没有.call方法，而且以一个整数为例，如果使用

	type(2){
	return Object.protope.toString.call(object)
	}

输出的形式为[Object Number]，这种形式对于我们判断类型时对比字符串是比较麻烦的，因而在函数之后添加`.slice(8,-1)`使输出字符串从第8个字符开始，输出结束从倒数第一个字符开始。
再添加`.toLowerCase()`使输出的字符串转化成小写。这样进行`===`的对比时右侧比较项的书写就更统一啦。