---
layout: post
title: "[javascript] final誤我一生 - js未來保留字"
date: 2012-02-17 17:50
comments: true
categories: javascript
---
## 問題
Rhino javascript debugger一直有一段敘述過不了

``` js
	var utc_current = self.options.begin + (self.options.final - self.options.begin)*offset/$('#homura').width();
```

可是明明真實的瀏覽器跑起來都正常運作，用jsfiddle的jslint看也沒問題：
<img src="http://farm8.staticflickr.com/7204/6890686877_931ed0154d_b.jpg" alt="jsfiddle說的"></img>
{% jsfiddle ddRsg %}

## 真相
用[online jslint](http://www.javascriptlint.com/online_lint.php)看,
{% img http://farm8.staticflickr.com/7056/6890686883_ff8c5d3848_b.jpg %}
突然想起來final好像是js保留字不能直接拿來當key，
實際上會因為瀏覽器有沒有處理而定。

## JS保留字
- abstract  else  instanceof  super  
- boolean  enum  int  switch  
- break  export  interface  synchronized  
- byte  extends					 let  this  
- case  false  long  throw  
- catch  final  native  thishrows  
- char  finally  new  transient  
- class  float  null  true						 
- const  for  package  try  
- continue  function  private  typeof							 
- debugger  goto  protected  var  
- default  if  public  void  
- debuggerlete  implements  return  volatile  
- do  import  short  while  
- double  in  static  with			

