---
layout: post
title : Angular笔记
categories: 前端
---
## LocationStrategy

angular路由可以使用两种url格式，

* 带`#`的 hash style,
* HTML 5 pushState style。

[pushSate](https://developer.mozilla.org/zh-CN/docs/Web/API/History_API) 是html5对于浏览器历史记录的新API。可以通过这套API实现ajax请求的后退功能。

但是angular里的链接是`<a href='foo'>`标签，如果想走angular的逻辑必须[修改浏览器点击`a`标签的默认行为](https://stackoverflow.com/q/1760096/5954068)。

这样一来在点击超链接时便不会直接向服务器发起请求，但是刷新页面时仍然会发，此时服务器没有对应的资源，便会返回404。

这也是 html5 pushSate风格的url的一个缺点，需要服务器的支持，具体做法就是在服务器找不到资源是[返回angular的默认页面](https://stackoverflow.com/a/40833154/5954068)。

### 参考

[PathLocationStrategy vs HashLocationStrategy in web apps](https://stackoverflow.com/q/34703343/5954068)

[intercept outgoing links Angular 4](https://stackoverflow.com/q/46560062/5954068)

