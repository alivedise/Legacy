---
layout: post
title: "[HTML] 多行tooltip(title)"
date: 2012-02-09 11:46
comments: true
categories: w3c
---

html原生tooltip(title屬性)顯示多行的方法：

``` html
	<span title="123&#13;456">test3</span>
```
殘念得是很難得的firefox有bug，多行會變成空白字元....
IE跟Chrome是正常的。

## jsfiddle

{% jsfiddle CUAh9 result,html %}

