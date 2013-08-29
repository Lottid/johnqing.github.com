---
layout: post
title: 非标准浏览器JSON解析实现
category: js
---

[parseJSON文件地址](https://github.com/Johnqing/parseJSON/blob/master/parsejson.js)

JSON的语法必须正确键必须用引号包裹：

{% highlight lua %}
{'x':1,'y':{'a':2}}
{% endhighlight %}

##使用##

+ JSON字符串解析为对象
{% highlight lua %}
JSON.parse(data);
{% endhighlight %}
+ JSON对象解析为字符串
{% highlight lua %}
JSON.stringify(data);
{% endhighlight %}