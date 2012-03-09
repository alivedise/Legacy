---
layout: post
title: "[JavascriptMVC] <翻譯+心得> JMVC導覽(1) introduction + $.Class"
date: 2012-02-02 09:46
comments: true
categories: javascriptmvc 
---

## 前言
本文以[https://gist.github.com/989117](https://gist.github.com/989117)
為基礎翻譯後再加上個人使用上的心得。


## 介紹
JavascriptMVC (JMVC)是一個基於jQuery的開放原始碼js框架。
它擁有完整的前端框架解決方案，包含打包工具，測試，代碼依賴管理，文件化，以及附帶許多有用的jQuery外掛。

JavascriptMVC的每一個項目都可以被獨立使用而不需要依賴其他項目。只看Class, Model, View, Controller部分的大小壓縮過只有7k左右，而且這之中的任何一個都還是能被獨立使用。
JavasriptMVC的輕巧及強大的獨立性使得它能應付複雜的大型web專案。

這個導覽 __只會__ 提到JavaScriptMVC的$.Class, $.Model, $.View, 和$.Controller.  下列是它們各自的意義:

 - <code>$.Class</code> - 基於js的類別化系統
 - <code>$.Model</code> - 傳統的model
 - <code>$.View</code> - 客戶端模版系統
 - <code>$.Controller</code> - jQuery元件工廠

JavaScriptMVC的命名取向不像傳統的 [Model-View-Controller](http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller#Concepts) 設計模式. $.Controller被用來創造一個傳統的view，例如翻頁按鈕會列表，同時也是傳統的controller－－作為傳統的model與傳統的view之間協調的角色。

## 安裝

### 方法一：官網下載

JavaScriptMVC can be used as a single download that includes the entire framework.  But since this chapter covers only the MVC parts, go to the [download builder](http://javascriptmvc.com/builder.html), check Controller, Model, and View's EJS templates and click download.  
		
The download will come with minified and unminified versions of jQuery and the plugins you selected.  Load these with script tags in your page:
		
	<script type='text/javascript' src='jquery-1.6.1.js'></script>  
	<script type='text/javascript' src='jquerymx-1.0.custom.js'></script> 

### 方法二：github
根據[JavascriptMVC on github](https://github.com/jupiterjs/javascriptmvc)的README:

0. 在自己帳號內開一個新git專案取名jmvc
1. Fork 以下這些project到自己的github帳號內

    http://github.com/jupiterjs/steal     
    http://github.com/jupiterjs/jquerymx  
    http://github.com/jupiterjs/funcunit  
    http://github.com/jupiterjs/documentjs

   可選的額外功能

    http://github.com/jupiterjs/mxui

2. 在自己的電腦上取回剛剛fork的javascriptmvc

    git submodule add git@github.com:_YOU_/steal.git steal
    git submodule add git@github.com:_YOU_/jquerymx.git jquery
    git submodule add git@github.com:_YOU_/funcunit.git funcunit
    git submodule add git@github.com:_YOU_/documentjs.git documentjs

3. 因為作者將主要功能都模組化的緣故，有四個子模組需要手動取回

    {% gist 1721116 %}

4. 可以開始玩了！ 


## Class

JMVC的Controller和Model繼承自Class的helper - $.Class. 要創造一個類別，只要呼叫 <code>$.Class(NAME, [classProperties, ] instanceProperties])</code>. 

    $.Class("Animal",{
		breathe : function(){
			console.log('breathe'); 
		}
	});

在上例中，Animal的instance都有<code>breathe()</code>這個method. 我們可以建立一個新的<code>Animal</code> instance而且呼叫它的<code>breathe()</code>像這樣:

	var man = new Animal();
	man.breathe();

如果你想要創造一個子類別, 只要把新類別名稱以及屬性用基礎類別呼叫即可:

	Animal("Dog",{
		wag : function(){
			console.log('wag');
		}
	})

    var dog = new Dog;
	dog.wag();
	dog.breathe();

### Instantiation - 物件化

當一個新的物件物體被創造時, 它首先會執行這個類別的<code>init</code>函式, 將建構子帶的參數傳給init:

	$.Class('Person',{
		init : function(name){
			this.name = name;
		},
		speak : function(){
			return "I am "+this.name+".";
		}
	});
    
    var payal = new Person("Payal");
	assertEqual( payal.speak() ,  'I am Payal.' );

### 呼叫基礎類別函式(base method)

用<code>this._super</code>使用基礎類別的函式.  下面重寫(overwrite)了person類別的speak函式。

	Person("ClassyPerson", {
		speak : function(){
			return "Salutations, "+this._super();
		}
	});
    
    var fancypants = new ClassyPerson("Mr. Fancy");
	assertEquals( fancypants.speak() , 'Salutations, I am Mr. Fancy.')

### 代理 - proxies

Class的回呼函式會把this適當地設置(類似[$.proxy](http://api.jquery.com/jQuery.proxy/))。下面建立一個clicky類別然後計算它被click多少次。

	$.Class("Clicky",{
		init : function(){
			this.clickCount = 0;
		},
		clicked: function(){
			this.clickCount++;
		},
		listen: function(el){
			el.click( this.callback('clicked') );
		}
	})
    
    var clicky = new Clicky();
	clicky.listen( $('#foo') );
	clicky.listen( $('#bar') ) ;

### 靜態繼承 - static inheritance

Class可以定義靜態屬性跟類別。如下允許我們用<code>Person.findOne(ID, success(person) )</code>向伺服器端取得一個person個體。成功的話會回傳一個Person個體。

	$.Class("Person",{
		findOne : function(id, success){
			$.get('/person/'+id, function(attrs){
				success( new Person( attrs ) );
			},'json')
		}
	},{
		init : function(attrs){
			$.extend(this, attrs)
		},
		speak : function(){
			return "I am "+this.name+".";
		}
	})

    Person.findOne(5, function(person){
		assertEqual( person.speak(), "I am Payal." );
	})

### 內觀 - Introspection

Class提供命名空間以及存取類別名稱以及命名空間的物件:

    $.Class("Jupiter.Person");

	Jupiter.Person.shortName; //-> 'Person'
	Jupiter.Person.fullName;  //-> 'Jupiter.Person'
	Jupiter.Person.namespace; //-> Jupiter
				    
	var person = new Jupiter.Person();
					    
	person.Class.shortName; //-> 'Person'

