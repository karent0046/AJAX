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

接受响应之后，第一步检查 status 属性，以确定响应已经成功返回。一般情况 HTTP 状态代码为 200 作为成功的标志。除了成功的状态代码，还有一些别的状态码：

|HTTP 状态码 |状态字符串 |说明|
|:---|:---|:---|
|200 |OK |服务器成功返回了页面|
|400 |Bad Request |语法错误导致服务器不识别|
|401 |Unauthorized |请求需要用户认证|
|404 |Not found |指定的 URL 在服务器上找不到|
|500 |Internal Server Error |服务器遇到意外错误，无法完成请求|
|503 |ServiceUnavailable |服务器过载或维护导致无法完成请求|

## 同步请求

同步请求步骤:
同步：

1、得到核心对象XMLHttpRequest对象

	var xhr = new XMLHttpRequest();
 
2、准备/打开请求

	open(请求类型GET/POST,请求的路径,是否异步true/false);
  
3、发送请求

	send(参数/null);
  
	注：如果是get请求，参数直接跟在请求路径后面，send()方法中设置null;
  
  ```
  	<script type="text/javascript">
		// 1、得到核心对象XMLHttpRequest对象
		var xhr = new XMLHttpRequest();
		console.log(xhr);
		// 2、准备/打开请求  open(请求类型GET/POST,请求的路径,是否异步true/false);
		xhr.open("GET","js/data.json?uname=zhangsan&uage=10",false); // 同步请求
		// 3、发送请求  send(参数/null);
		xhr.send(null);
		// 4、解析响应数据
		if (xhr.status == 200) { // 1、判断响应是否成功 status=200
			// 2、得到后台响应数据  responseText
			console.log(xhr.responseText);
			var user = JSON.parse(xhr.responseText);
			console.log(user);
			console.log(user.uname);
		} else {
			alert("失败状态码：" + xhr.status + "，失败原因：" + xhr.statusText);
		}
		
	</script>
  ```
  
  
		如果是post请求，有参数则设置参数，无参数设置为null;
    
4、解析响应数据

	1、判断响应是否成功 status=200 （404=未找到资源;500=服务器异常;200=成功）
      
	2、得到后台响应数据  responseText
