# AJAX笔记


## AJAX

### 1.概念
“Ajax：A newApproach to Web Applications”是 Asynchronous JavaScript + XML 的简写。这种技术能够向服务器请求额外的数据而无须卸载页面(即刷新)，会带来更好的用户体验。

### 2.XMLHttpRequest
Ajax 技术核心是 XMLHttpRequest 对象(简称 XHR)
注意:虽然 Ajax 中的 x 代表的是 XML，但 Ajax 通信和数据格式无关，也就是说这种技术不一定使用 XML。可以用PHP,json等等
创建 XHR 对象可以直接实例化 XMLHttpRequest
```
var xhr = new XMLHTTPRequest();
alert(xhr);
```
### 3.属性

当请求发送到服务器端，收到响应后，响应的数据会自动填充 XHR 对象的属性。一共有四个属性：

|属性名|说明|
|:---|:---|
|responseText| 作为响应主体被返回的文本|
|responseXML |如果响应主体内容类型是"text/xml"或"application/xml"，则返回包含响应数据的XML DOM 文档|
|status| 响应的 HTTP 状态|
|statusText| HTTP 状态的说明|
