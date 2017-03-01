#AJAX<br />

##XMLHttpRequest对象<br />
###创建XHR对象
```
	var xmlhttp;
		if (window.XMLHttpRequest)
		  {// code for IE7+, Firefox, Chrome, Opera, Safari
		  xmlhttp=new XMLHttpRequest();
		  }
		else
		  {// code for IE6, IE5
		  xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
 	}	
```
###XHR对象的方法
 - open(method,url,async)<br />
 	规定请求的类型、URL 以及是否异步处理请求。
	- method：请求的类型；GET 或 POST
    - url：文件在服务器上的位置
    - async：true（异步）或 false（同步）
 - send(string)
 	将请求发送到服务器。
	- string：仅用于 POST 请求<br />
	
###XHR对象的属性
 - onreadystatechange 存储函数（或函数名），每当 readyState 属性改变时，就会调用该函数。
 - readyState<br />
 	存有 XMLHttpRequest 的状态。从 0 到 4 发生变化。
	- 0: 请求未初始化 尚未调用open()方法
	- 1: 服务器连接已建立 已经调用open()方法，但尚未调用send()方法
	- 2: 请求已接收  已经调用send()方法，但尚未收到响应
	- 3: 请求处理中 已经收到部分响应数据 
	- 4: 请求已完成，且响应已就绪	
 - 服务器响应 <br />
如需获得来自服务器的响应，请使用 XMLHttpRequest 对象的 responseTex、responseXML、responseBody、responseStream 属性。其中我们需要深入了解的，只有 responseText 和 responseXML 两种，至于
responseBody和responseStream，基本上可以不用考虑。
    - responseText 将响应信息作为字符串返回
    - responseXML 将响应信息格式化为XMLDOM对象并返回
    - responseBody 将响应信息以unsigned byte 数组的形式返回
    - responseStream 将响应信息以IStream 对象的形式返回

###实例
```
	function loadXMLDoc()
		{
		var xmlhttp;
		if (window.XMLHttpRequest)
		  {// code for IE7+, Firefox, Chrome, Opera, Safari
		  xmlhttp=new XMLHttpRequest();
		  }
		else
		  {// code for IE6, IE5
		  xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
		  }
		xmlhttp.onreadystatechange=function()
		  {
		  if (xmlhttp.readyState==4 && xmlhttp.status==200)
		    {
		    document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
		    }
		  }
		xmlhttp.open("GET","/ajax/test1.txt",true);
		xmlhttp.send();
	}
```
