---
layout: post
title: "[javascriptMVC] Forum 問答"
date: 2012-02-24 01:53
comments: true
categories: javascriptMVC 
---
### 如何手動觸發model update? 讓'{model} updated'可以被想要接受的人接收
* [出處](https://forum.javascriptmvc.com/topic/how-to-invoke-model-foo-updated-after-model-update)
* 答案
``` js
	modelInstanceVariable.updated({});
``` 

### 可以讓view自動聽model更新自己改變自己嗎？

	不行。你應該用controller去更新view。

### 如何除錯./js
``` bash
	./js -d  ##開啟Rhino javascript debugger

	##之後針對要除錯的js下load

	load('steal/pluginifyjs')
	steal.build.pluginify('alive/gundam',{});
	## 記得設中斷點
```

