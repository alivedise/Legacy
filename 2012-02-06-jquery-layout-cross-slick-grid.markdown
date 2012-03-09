---
layout: post
title: "[jQuery]UI.layout*SlickGrid - 使SlickGrid在layout改變大小時能自動filter高度"
date: 2012-02-06 13:42
comments: true
categories: jquery
---

目前只有一種作法，利用publish/subscribe告訴SlickGrid要去追parent的高度

``` js
$.subscribe("units/set_grid_height", function (new_height) {
	grid_opts.height = new_height;
	resize();
});

// ...

// grid = the jQuery element that represents the SlickGrid
// slick = the instantiated slickgrid
function resize() {
  grid.css('height', grid_opts.height);
  slick.resizeCanvas();
}
```

``` js
layout = $('body').layout({
	center: { 
		onresize: function (name, el, state, opts, layout_name) { 
			$.publish("units/set_grid_height", [state.innerHeight]);
		}
	}
});

$.publish("units/set_grid_height", [layout.state.center.innerHeight]);

```


