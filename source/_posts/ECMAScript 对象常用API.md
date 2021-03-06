---
title: ECMAScript 对象常用API
date: 2018-02-24 20:45:02
categories: JavaScript
tags:
---

#### `Object`

属性

	* Object.length //值为1。
	* Object.prototype //可以为所有 Object 类型的对象添加属性。

方法
	
	* Object.assign(新对象, 源对象) //通过复制一个或多个对象来创建一个新对象。
	* Object.create(proto) //使用指定的原型对象和属性创建一个新对象。
	
	* Object.entries(obj) //返回给定对象自身可枚举属性的[key, value]数组。
	* Object.getPrototypeOf(obj) //返回指定对象的原型对象。
	
	* Object.freeze(obj) //冻结对象：其他代码不能删除或更改任何属性。
	* Object.seal(obj) //防止其他代码删除对象的属性。
	
	* Object.is(value1, value2) //比较两个值是否相同。所有 NaN 值都相等（这与==和===不同）。
	
	* Object.keys(obj) //返回一个包含所有给定对象自身可枚举属性名称的数组。
	* Object.values(obj) //返回给定对象自身可枚举值的数组。
	


---
 
#### `Function`

属性

	* Infinity //代表正的无穷大的数值。
	* NaN //指示某个值是不是数字值。
	* undefined //指示未定义的值。

方法

	* decodeURI(URI) //解码某个编码的 URI。
	* decodeURIComponent(URI) //解码一个编码的 URI 组件。
	* encodeURI(string) //把字符串编码为 URI。
	* encodeURIComponent(string) //把字符串编码为 URI 组件。
	* escape(string) //对字符串进行编码。
	* isFinite(value) //检查某个值是否为有穷大的数。
	* isNaN(value) //检查某个值是否是数字。
	* parseFloat(string) //解析一个字符串并返回一个浮点数。只解析十进制数。
	* parseInt(string,radix) //解析一个字符串并返回一个整数。
		parseInt('123', 5) // 返回38 => 1*5^2 + 2*5^1 + 3*5^0 = 38
	* Number(object) //把对象的值转换为数字。
	* String(object) //把对象的值转换为字符串。
	* eval(string) //将传入的字符串当做 JavaScript 代码进行执行。
	
	举例 
		eval('var a = 1;')
		a // 1

---

#### `Array`

属性

	* constructor //返回创建数组对象的原型函数。
	* length //设置或返回数组元素的个数。
	* prototype //表示 Array 构造函数的原型，并允许您向所有 Array 对象添加新的属性和方法。

方法

	* Array.map(function(currentValue, index, arr), thisValue) //创建一个新数组，其结果是该数组中的每个元素(按照原始数组元素顺序)都调用一个提供的函数后返回的结果。
	* Array.forEach(function(currentValue, index, arr), thisValue) //同 map() 一样，但没有返回值。
		function(currentValue, index, arr) //必需参数。
		currentValue //必需。当前位置的值。

	* Array.join('分隔符') //以参数作为分隔符，将所有数组成员组成一个字符串返回。
	* Array.concat(arr1,arr2...) //用于合并两个或多个数组。它将新数组的成员，添加到原数组成员的后部，返回一个新数组，原数组不变。
	
	* Array.filter(function) //用于过滤数组成员，满足条件的成员组成一个新数组返回。
	* Array.reduce(function(之前的结果, 当前变量),当前的初值) //按原始顺序依次处理数组的每个成员，最终累计为一个值。
	
	* Array.sort(function) //对数组成员进行排序。排序后，原数组将被改变。
	* Array.reverse() //用于颠倒数组中元素的顺序，返回改变后的数组。该方法会改变原数组。
	
	* Array.push(item1,item2...) //在数组的末端添加一个或多个元素，并返回添加新元素后的数组长度。该方法会改变原数组。
	* Array.unshift(item1,item2...) //用于在数组的第一个位置添加一个或多个元素，并返回添加新元素后的数组长度。该方法会改变原数组。
	
	* Array.slice(start, end) //用于提取原数组的一部分，返回一个新数组，原数组不变。
	* Array.pop() //用于删除数组的最后一个元素，并返回该元素。该方法会改变原数组。
	* Array.shift() //用于删除数组的第一个元素，并返回该元素。该方法会改变原数组。
	* Array.splice(start, length, item1,item2...) //用于删除原数组的一部分成员，并可以在被删除的位置添加入新的数组成员，返回值是被删除的元素。该方法会改变原数组。
	
	* Array.some(function) //用来判断数组成员是否符合某种条件。一项满足则整个返回 true 
	* Array.every(function) //用来判断数组成员是否符合某种条件。所有项满足则整个返回 true
	
	* Array.indexOf(item, start) //按原始顺序依次搜索数组中的元素，并返回它所在的位置。如果在数组中没找到字符串则返回 -1。
	
	* Array.valueOf() //返回数组对象的原始值。
	* Array.toString() //把数组转换为字符串，并返回结果。


---

#### `Date`

定义一个事件对象

	var Udate = new Date()
	//初始值：当前时间(当前电脑系统时间)。
	
	//日期设置成对应的星期
	<script type="text/javascript">
		 var mydate=new Date();
		 var weekday=["星期日","星期一","星期二","星期三","星期四","星期五","星期六"];
		 var mynum = mydate.getDay()
		 document.write("今天是:"+weekday[mynum]);
	</script>

属性
	
	* constructor //返回对创建此对象的 Date 函数的引用。
	* prototype //表示 Date 构造函数的原型，并允许您向所有 Date 对象添加新的属性和方法。

方法 
	
	* Udate.get/setDate() //返回/设置日期，返回的是0-6的数字，0 表示星期天。
	* Udate.get/setFullYear() //返回/设置年份，用四位数表示
	* Udate.get/setYear() //返回/设置年份
	* Udate.get/setMonth() //返回/设置月份。0：一月...11：十二月
	* Udate.get/setHours() //返回/设置小时，24小时制。
	* Udate.get/setMinutes() //返回/设置分钟数
	* Udate.get/setSeconds() //返回/设置秒钟数
	* Udate.get/setTime() //返回/设置时间（单位为毫秒）

---

#### `String`

属性

	* constructor //对创建该对象的函数的引用
	* length //字符串的长度
	* prototype //表示 String 构造函数的原型，并允许您向所有 String 对象添加新的属性和方法。

方法

	* String.toLowerCase() //把字符串转换为小写。
	* String.toUpperCase() //把字符串转换为大写。
	
	* String.charAt(index) //返回在指定位置的字符。
		//如果没有提供索引，charAt() 将使用0。
		
	* String.indexOf(substring, start) //返回某个指定的字符串值在字符串中首次出现的位置。没有找到匹配的字符串则返回 -1。
		//substring 要搜索的字符串值
		//start 可选参数，开始搜索的位置。
	
	* String.split(separator,limit) //把字符串分割为字符串数组。
		//separator 以此参数作为分割符
		//limit 可选参数，分割的次数
	
	* substring(start,end) //提取字符串中两个指定的索引号之间的字符（不包括 end 的字符）。
	* substr(start,length) //从起始索引号提取字符串中指定数目的字符。

	* String.match(regexp) //检索字符串 String Object，以找到一个或多个与 regexp 匹配的文本。
	
	* String.replace(searchvalue,newvalue) //用于在字符串中用一些字符替换另一些字符 
	
---

#### `Boolean`

属性

	* constructor //返回对创建此对象的 Boolean 函数的引用
	* prototype //表示 Boolean 构造函数的原型，并允许您向所有 Boolean 对象添加新的属性和方法。
	
方法

	* toString() //把布尔值转换为字符串，并返回结果。
	* valueOf() //返回 Boolean 对象的原始值。

---

#### `Number`

属性

	* constructor //返回对创建此对象的 Number 函数的引用。
	* NaN //非数字值。
	* prototype //表示 Number 构造函数的原型，并允许您向所有 Number 对象添加新的属性和方法。

方法

	* toString() //把数字转换为字符串，使用指定的基数。
	* valueOf() //返回一个 Number 对象的基本数字值。

---

#### `Math`

方法

	* Math.abs(x) //返回 x 的绝对值。
	* Math.ceil(x) //对 x 向上取整计算，它返回的是大于或等于函数参数，并且与之最接近的整数。
	* Math.floor(x) //和 ceil(x) 相反
	* Math.max(x,y,z,...,n) //返回 x,y,z,...,n 中的最高值。
	* Math.min(x,y,z,...,n) //返回 x,y,z,...,n中的最低值。
	* Math.random() //返回 0 ~ 1 之间的随机数。
	* Math.round(x) //把数四舍五入为最接近的整数。
	* Math.sqrt(x) //返回数的平方根。
	* Math.pow(x,y) //返回 x 的 y 次幂。

举例

	Math.sqrt(4) // 2
	Math.sqrt(-4) // 负值返回 NaN
	
	Math.pow(2,3) // 8

---