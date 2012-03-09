---
layout: post
title: "[javascriptMVC] Class init"
date: 2012-02-24 01:35
comments: true
categories: javascriptmvc
---
``` js
	$.Controller('Alive',{
		//static init
		init: function(){
			steal.dev.log('The class init will be invoked whenever you declare a class');
		}
	},{
		init: function(){
			steal.dev.log('The instance init will be invoked whenever you declare a new instance');
		}
	});

	/*Console: The class init will be invoked whenever you declare a class */
	new alive(element);
	/*Console: The instance init will be invoked whenever you declare a new instance */
```




