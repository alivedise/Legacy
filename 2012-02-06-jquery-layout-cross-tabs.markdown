---
layout: post
title: "[jquery] jQuery layout X jQuery UI Tabs的應用"
date: 2012-02-06 10:05
comments: true
categories: jquery 
---

jQuery layout是一套幫助RD排版的工具，
現在遇到一個需求是在某個layout出來的版面中塞jQuery UI TABS，
會有scrollbar顯示的問題。

在jQuery layout官方範例有特別作一個tab結合的範例，看看它怎麼處理這個問題：
[原始網址](http://layout.jquery-dev.net/demos/tabs.html)

## jsfiddle

{% jsfiddle tmmuU %}

## source

``` js jquery.layout-latest.js
322             ,   contentSelector:        ".ui-layout-content" // INNER div/element to auto-size so only it scrolls, not the entire pane!                      
323         ,   contentIgnoreSelector:  ".ui-layout-ignore" // element(s) to 'ignore' when measuring 'content'
324         ,   findNestedContent:      false       // true = $P.find(contentSelector), false = $P.children(contentSelector)
325         //  GENERIC ROOT-CLASSES - for auto-generated classNames
326         ,   paneClass:              "ui-layout-pane"    // border-Pane - default: 'ui-layout-pane'
327         ,   resizerClass:           "ui-layout-resizer" // Resizer Bar      - default: 'ui-layout-resizer'
```

也就是，利用<code>contentSelector</code>跟<code>findNestedContent</code>告訴layout plugin我要把contentSelector的內容視作layout-pane的本體，
在改變大小時候應該去改變它而不是整個layout-pane。

