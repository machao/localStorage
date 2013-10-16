localStorage
============

高度兼容的localStorage实现，完美支持IE系列浏览器，并提供简化的二次包装接口。

**支持浏览器**

	IE6 / IE7 / IE8 / IE9 / IE10 / IE11 / FireFox / Chrome / Opera / Safri

**使用方法**

在head标签内引入storage.js即可。

	<script src='storage.js'></script>
**接口示例**

	window.LS.set("hello", "world"); //设置
	window.LS.get("hello");			 //读取，如果没有内容，则返回 undefined
	window.LS.remove("hello");		 //删除
	window.LS.clear();				 //清空
	window.LS.each(function(key, value){	//遍历
		// do something
	});
	var list = window.LS.obj();		  //获取本地存储列表对象
	var listNum = window.LS.length;	  //获取本地存储数量

如果在storage.js之前有jQuery，则会为jQuery添加 jQuery.LS 接口，跟 window.LS 功能一致。  

**原理说明**

![本地存储兼容性](http://pic002.cnblogs.com/images/2012/422834/2012070316413785.jpg "本地存储兼容性")

上图为localStorage兼容性描述，在IE下，有一个名为userData的东东可以模拟实现localStorage的接口。<br/>

但是有些高版本的IE虽然有localStorage，但是有诸多的问题，本组件通过不断的优化探测方案，选择一个<br/>
合适的方案来实现模拟接口，为不支持localStorage的，或localStorage有问题的IE浏览器实现一个模拟对<br/>
象，然后创建一个统一的接口 window.LS 来提供相关功能。

 * 原生localStorage接口有点啰唆，所以 window.LS 提供的接口都非常简单易懂。<br/>
 * 如果你不喜欢这个包装接口，本组件为不支持localStorage的浏览器添加了window.localStorage接口，<br/>
也可以使用，不过你将遇到所有原生loacalStorage可能遇到的问题。

**已知问题**

 * 原生本地存储的key是区分大小写的，模拟对象不区分（因为userData不区分key的大小写）
 * 模拟对象的 clear 方法仅仅能清理通过本组件设定的数据
 * 模拟对象的实际的存储容量跟原生本地存储有差异
 * 模拟对象不支持任何localStorage事件件
