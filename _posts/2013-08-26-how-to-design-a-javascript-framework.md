---
layout: post
title: 如何设计一个javascript框架？
---

> 做为一个多年的开发者，你是否有考虑过设计一个属于自己的框架？

*随口乱吹，勿喷勿喷！*


##简单的结构如下：##

1. 语言拓展
2. DOM拓展
3. ajax拓展
4. 动画
5. 脚本管理
6. 组件

###语言拓展###

大部分框架都提供了这块的内容。语言拓展应该是基于ECMAScript来工作的，而且要保证运行在任何环境下，而不是局限在浏览器环境下。

###DOM拓展###

浏览器做为现在最大的平台，所以大部分框架都会首先做到他的兼容。DOM拓展要首先基于webkit内核浏览器来进行，ie等低版本浏览器，可做相应的hack。
DOM拓展主要的目的是做到浏览器的兼容性消除，请勿拓展一些用处很小的奇怪对象。

###ajax拓展###

js的兴起，就是因为ajax带来的优势，所以如果你想更好的推广你的框架，优秀的ajax接口是必须的。
这款封装的主要目的，也是要做到浏览器的兼容性，XMLHttpRequest在ie6下必须使用ActiveX，而ActiveX又有多个版本。
还有get和post传参不同带来的一系列问题，以及success和error等状态的监控

###动画###

在计算机性能越来越强大，用户对于体验要求越来越严苛的年代。炫酷的效果代码的是极致的享受，所以一款优秀的js框架不能缺少一个优秀的动画模块。

###脚本管理###

在前端越来越专业化的年代，很多同学都是从服务端转变而来。所以很多人都喜欢使用C++或者java的 `import` / `include` 等方法就管理当前的脚本。
目前这块有单独的框架来实现。

###组件###

jQuery出名，除了优秀的dom操作外，还有其海量的组件。所以嘛，一款牛逼的框架，应该有很多优秀的组件支持。


##框架设计123##

###放开那个prototype###

很多人都喜欢对prototype做拓展，但是请注意。
你不能保证将来会不会出现一个跟你命名的方法相同的拓展，而且你也不能保证别的框架不去修改此方法。

特别需要注意的是，Object和Array这两个对象的prototype扩展格外的危险，
对Object来说，如果Object被修改，那么框架的使用者将无法创建一个未被修改的干净的对象，这是一个致命的问题，尤其如果你的使用者喜欢用for in来反射一个对象的属性。

Array.prototype修改的危险来自js一个不知有意还是无意的小小设计，对原生的Array来说，任何情况下for和for in的遍历结果是相同的，而因为无法控制自定义的属性是不可枚举的，任何Array.prototype的修改都会破坏这种特性。

###看好你家的“狗”###

好的框架要保证，自己的命名空间不被别人污染，也要保证不污染别人，所以请看好你家的“狗”。

###废话连篇什么的最讨厌了###

在你的框架设计中，请不要实现无用的方法。

{% highlight javascript %}
var add = function(a, b){
	return a + b;
}
{% endhighlight %}

##总结##

也许不全，也许说的不好，但是我自己的一点小小感悟。

##广告##

大家一起来搞[n.js](https://github.com/Johnqing/n.js)吧!