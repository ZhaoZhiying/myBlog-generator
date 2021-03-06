---
title: DOM 事件
date: 2018-01-04 15:31:21
categories: JavaScript
tags:
---


* `javascript`与`HTML`的交互是通过事件实现的。
* 事件就是文档或浏览器窗口中发生的一些特定的交互瞬间。
* 事件流(又叫事件传播)描述的是从页面中接收事件的顺序。

------

### `DOM 事件流`
当浏览器发展到第四代时，浏览器开发团队遇到一个问题：页面的哪一部分会拥有某个特定的事件？后来`IE` `Netscape`提出了完全相反的事件流的概念。

##### 事件冒泡
`IE`的事件叫做事件冒泡。即事件开始时由文档中嵌套层次最深的那个节点接收，然后逐级向上传播到文档。

举例

	<!DOCTYPE html>
	<html>
	<head>
		<title>举例</title>
	</head>
	<body>
		<div id="myDiv">click me</div>
	</body>
	</html>
	//单击 <div> 时，传播顺序为：<div> <body> <html> document

##### 事件捕获 
`Netscape`的事件叫做事件捕获。即事件开始时由`document`接收，逐级向下传播到文档中嵌套层次最深的那个节点。

按前面例子：
	
	//单击 <div> 时，传播顺序为： document <html> <body> <div>
	

##### `DOM Level 2 事件`规定的事件流包括三个阶段：

	（1）事件捕获阶段：事件从 Document 节点自上而下向目标节点传播的阶段；
	（2）事件目标阶段：真正的目标节点正在处理事件的阶段；
	（3）事件冒泡阶段：事件从目标节点自上而下向 Document节点传播的阶段。
	
------

### DOM 事件发展
#### `DOM Level 0 事件`
	
主要分为2个：

1.标签内写 `onclick` 事件

	<button id="button1" onclick="console.log('hi')">A</button>

2.`JS` 里写 `onclick = function (){}` 函数

	document.getElementById("button1").onclick = function print(){
		console.log('hi')
	}
	

#### `DOM Level 1 事件`
	
`DOM Level 1`于1998年10月1日成为 `W3C` 推荐标准。但是标准中并没有定义事件相关的内容，所以没有所谓的 `DOM Level 1` 事件模型。

#### `DOM Level 2 事件`

* 在`DOM Level 0 事件`的基础上弥补了一个处理程序无法同时绑定多个处理函数的缺点，允许给一个处理程序添加多个处理函数。`DOM Level 2 事件`只定义了两个方法，分别用来绑定和解绑事件：

```	
addEventListener() 对应 IE8 中的 attachEvent()
removeEventListener() 对应 IE8 中的 detachEvent()

//都有三个参数
参数1：事件名（不要使用 "on" 前缀）</br>
参数2：事件触发时执行的函数</br>
参数3：事件是否在捕获或冒泡阶段执行（第三个参数为 true，为捕获阶段；不传第三个参数或者传 false 为冒泡阶段）</br>
	
//如果又有捕获又有冒泡，那就不区分捕获还是冒泡，按照代码顺序。
```


HTML

	
	<div id="grand1">
	爷爷
	 <div id="parent1">
	  爸爸
	   <div id="child1">
	    儿子
	   </div>
	 </div>
	</div>


JS

	grand1.addEventListener('click', function fn1(){
	  console.log('爷爷')
	},true)//捕获阶段
	parent1.addEventListener('click', function fn2(){
	  console.log('爸爸')
	},false)//冒泡阶段
	child1.addEventListener('click', function fn3(){
	  console.log('儿子')
	})//冒泡阶段
	//当点击‘儿子’时，打印的顺序是：爷爷、儿子、爸爸


#### `DOM Level 3 事件`

`DOM Level 3 事件`在`DOM Level 2 事件`的基础上添加了更多的事件类型，全部类型如下：

	UI事件，当用户与页面上的元素交互时触发，如：load、scroll
	焦点事件，当元素获得或失去焦点时触发，如：blur、focus
	鼠标事件，当用户通过鼠标在页面执行操作时触发如：dbclick、mouseup
	滚轮事件，当使用鼠标滚轮或类似设备时触发，如：mousewheel
	文本事件，当在文档中输入文本时触发，如：textInput
	键盘事件，当用户通过键盘在页面上执行操作时触发，如：keydown、keypress
	合成事件，当为IME（输入法编辑器）输入字符时触发，如：compositionstart
	变动事件，当底层DOM结构发生变化时触发，如：DOMsubtreeModified
	
	同时DOM3级事件也允许使用者自定义一些事件。
	
---

#### 常用事件归纳

##### 鼠标事件

	* onclick //当用户点击某个对象时调用的事件句柄。
	* oncontextmenu //在用户点击鼠标右键打开上下文菜单时触发。
	* ondblclick //当用户双击某个对象时调用的事件句柄。
	* onmousedown //鼠标按钮被按下。
	* onmouseenter //当鼠标指针移动到元素上时触发。
	* onmouseleave //当鼠标指针移出元素时触发
	* onmousemove //鼠标被移动。	
	* onmouseover //鼠标移到某元素之上。	
	* onmouseout //鼠标从某元素移开。	
	* onmouseup //鼠标按键被松开。

##### 键盘事件

	* onkeydown //某个键盘按键被按下。	
	* onkeypress //某个键盘按键被按下并松开。
	* onkeyup //某个键盘按键被松开。		

##### 表单事件

	* onblur //元素失去焦点时触发	
	* onchange //该事件在表单元素的内容改变时触发( <input>, <keygen>, <select>, 和 <textarea>)	
	* onfocus //元素获取焦点时触发	
	* onfocusin //元素即将获取焦点时触发	
	* onfocusout //元素即将失去焦点时触发	
	* oninput //元素获取用户输入时触发	
	* onreset //表单重置时触发	
	* onsearch //用户向搜索域输入文本时触发 ( <input="search">)
	* onselect //用户选取文本时触发 ( <input> 和 <textarea>)
	* onsubmit //表单提交时触发

##### 动画事件

	* animationend //该事件在 CSS 动画结束播放时触发 
	* animationiteration //该事件在 CSS 动画重复播放时触发
	* animationstart //该事件在 CSS 动画开始播放时触发

##### 过渡事件

	* transitionend //该事件在 CSS 完成过渡后触发。

##### 事件对象

	* preventDefault() //通知浏览器不要执行与事件关联的默认动作。
	* stopPropagation() //不再派发事件。

##### 目标事件对象

	* addEventListener() //允许在目标事件中注册监听事件(IE8 = attachEvent())	
	* removeEventListener() //运行一次注册在事件目标上的监听事件(IE8 = detachEvent())

---	
	






	