---
layout: AJAX
title: 是什么？
date: 2018-01-28 23:32:06
tags:
---
#### 历史背景
##### 如何发请求？
* `form`可以发请求，但是会刷新页面或新开页面
* `a`标签可以发`get`请求，但是会刷新页面或新开页面
* `img` 可以发`get`请求，但是只能以图片的形式展示
* `link`可以发`get`请求，但是只能以 `CSS` `favicon` 的形式展示
* `script`可以发`get`请求，但是只能以脚本的形式运行
 
那么问题来了，有没有什么方式可以实现？

* `get` `post` `put` `delete` 请求都行
* 想以什么形式展示就以什么形式展示

##### 微软的突破
`IE 5` 率先在 `JS` 中引入 `ActiveX` 对象（API），使得 `JS` 可以直接发起 HTTP 请求。
随后 `Mozilla` `Safari` `Opera` 也跟进（抄袭）了，取名 `XMLHttpRequest`，并被纳入 `W3C 规范`

##### `AJAX`诞生
2005年，Jesse James Garrett 发表了一篇在线文章，在这篇文章里介绍了一种技术，叫 `AJAX`，是对 `Asynchronous JavaScript + XML` 的简写，译为异步的`JavaScript`和`XML`。

1. 使用 `XMLHttpRequest` 发请求
2. 服务器返回 `XML` 格式的字符串 (`XML`后来被`JSON`取代)
3. `JS` 解析 `XML`，并更新局部页面

---

#### `XMLHTTPRequest`

如何使用原生`JS`来发送`AJAX`请求？（`XMLHTTPRequest`）

```
//main.js
myButton.addEventListener('click', (e)=>{
 let request = new XMLHttpRequest()
 request.onreadystatechange = () =>{ 
     if(request.readyState === 4){
         console.log('请求响应完毕')
         if(request.status >= 200 && request.status < 300){
             console.log('请求成功')
         }else if(request.status >= 400){
             console.log('请求失败')
         }
     }
 }
 request.open('GET', '/xxx') // 配置request
 request.send()
})
    
// 后端代码（XML）
}else if(path === '/xxx'){
 response.statusCode = 200
 response.setHeader('Content-Type', 'text/XML')
 response.write(`
<note>
  <to>糖糖</to>
  <from>照照</from>
   <heading>hellow你好吗</heading>
   <body>hellow你好吗衷心感谢珍重再见期待再相逢</body>
 </note>
 `)
 response.end()
}
   
// 后端代码（JSON）
}else if(path === '/xxx'){
 response.statusCode = 200
 response.setHeader('Content-Type', 'text/XML')
 response.write(`
  {
     "note":{
        "to": "糖糖",
        "from": "照照",
        "heading": "哈喽",
        "content": "你好吗"
      }
    }
 `)
 response.end()
}
```    

`readyState`的五种状态，重点记住`4`

<img src='https://i.loli.net/2018/01/29/5a6eeb46a0ca4.png
'>

##### `XML`
* 曾有一段时间，`XML`是互联网上传输结构化数据的事实标准。

* 但是`XML`过于烦琐、冗长。为解决这个问题，涌现了一些方案。直到 2006年，`Douglas Crockford` 提出了 `JSON` 语言。

---

#### `JSON`
`JSON`是`JavaScript Object Notation`的简称，它是一种表示结构化数据的格式。相比`XML`，`JSON`是在`JavaScript`中读写结构化数据的更好的方式。因为可以把`JSON`

##### `JSON` 与 `JavaScript` 的关系
`JSON` 和`JavaScript`是两种不同的语法，`JSON`参考了`JavaScript`。

##### `JSON` 与 `JavaScript` 的区别
1.`JSON`没有`function`和`undefined`。<br/>
2.`JSON`字符串首尾必须使用双引号。<br/>

```
"Hello world"
```
3.与`JavaScript`的对象字面量相比，`JSON`对象有两处不同：<br/>

* `JSON`没有变量的概念，一个对象以`{`开始并以`}`结束。并且没有末尾的分号。
* `JSON`中对象的属性名必须加双引号。
	
```
{"name": "zhao", "age": 18}
```

4.`JSON`的数组也没有变量和分号，一个数组以`[`开始并以`]`结束。

```
["name", 18, true]
```

5.`JSON`中没有原型链。

---
#### 同源策略与`CORS`跨域
##### 同源策略
只有 协议+端口+域名 一模一样才允许发 `AJAX` 请求，如下：

```
http://baidu.com 可以向 http://www.baidu.com 发 AJAX 请求吗 //no
http://baidu.com:80 可以向 http://baidu.com:81 发 AJAX 请求吗 //no
```

##### `CORS`

* 只有 协议+端口+域名 一模一样才允许发 `AJAX` 请求
* `CORS` 可以告诉浏览器，我俩一家的，别阻止他
* `CORS`是`Cross-Origin Resource Sharing`的简称，译为跨源资源共享。

```
// 后端代码（JSON）
}else if(path === '/xxx'){
 response.statusCode = 200
 response.setHeader('Content-Type', 'text/XML')
 response.setHeader('Access-Control-Allow-Origin', 'http://frank.com:8001')//CORS
 response.write(`
  {
     "note":{
        "to": "糖糖",
        "from": "照照",
        "heading": "哈喽",
        "content": "你好吗"
      }
    }
 `)
 response.end()
}
```

---

参考：[写代码啦] (https://xiedaimala.com/)