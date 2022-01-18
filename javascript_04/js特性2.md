### 四、DOM操作（下）

3. 节点操作

   * 创建节点  `document.createElement('标签名称')`

   * 插入节点  `父节点.appendChild(子节点)`  或 `父节点.insertBefore(要插入的节点，排在哪个子节点前面)`

   * 删除节点 `父节点.removeChild(子节点)`  或 `节点.remove()`

   * 替换节点  `父节点.replaceChild(新子节点，旧子节点)`

   * 克隆节点  `节点.cloneNode(是否顺带克隆它子节点)`

     ```html
     <!DOCTYPE html>
     <html>
     <head>
     	<meta charset="utf-8">
     	<title>DOM节点操作</title>
     </head>
     <body>
     
     	<div id='original_div'>
     		<p>页面已经存在的标签</p>
     	</div>
     
     	<script type="text/javascript">
     		
     		// 创建节点
     		var div = document.createElement('div')
     
     
     		// 创建节点并插入已知节点
     		var span = document.createElement('span')
     		span.innerText = '创建好的span'
     		var oDiv = document.getElementById('original_div')
     		oDiv.appendChild(span)
     
     		// 将span添加到p标签前面
     		var p = document.querySelector('p')
     		oDiv.insertBefore(span,p)
     
     		// 删除p节点
     		oDiv.removeChild(p)
     
     	</script>
     
     </body>
     </html>
     ```

   

4. 获取元素的尺寸     

     `元素.offsetHeight`

     `元素.offsetWidth`

     `元素.clientHeight`
   
     `元素.clientWidth`  
   
     

### 五、js事件

常见事件类型：

![eventType](D:\Html&css\javascript\eventType.jpg)



1. 事件对象

   每一次接到事件，会用一个对象保存事件的触发对象，键盘按键，鼠标坐标等。要拿到这个对象，只需要在事件绑定时拿到形参：

   ```js
   div.onclick = function(e){
       console.log(e)
   }
   ```

   * 鼠标事件对象e内的信息：

     * 坐标信息：

       offsetX, offsetY(相对事件触发元素的坐标), 

       clientX, clientY（相对浏览器可视窗口的坐标）, 

        pageX, pageY（相对于页面文档流的坐标），

   * 键盘事件对象e的信息：

     * 键盘编码：e.keyCode

2. 事件传递顺序：

   *  结论： 事件由外部window -> document -> html -> outer -> center -> inner
   *  事件回去： inner-> center -> outer -> html -> document -> window

3. 阻止事件传播：

   `事件对象e.stopPropagation()`

    也可以用`e.target`判断事件目标做条件判断



### 六、面向对象

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>面向对象 构造函数使用</title>
</head>
<body>
		<script type="text/javascript">
			/**
			 * 构造函数和普通函数没有区别，但是在使用的时候需要与new关键字一起，类似java类的使用
			 * 规范：构造函数定义时，首字母应大写
			 * 构造函数中的this代表调用方 
			 * 构造函数内部不要写return,因为"return 基本数据类型" 无效,还会破坏构造函数的功能
			 * 
			 * 调用构造函数时，如果不用传入参数则可省略圆括号
			 * 
			 * 构造函数的注意点：
			 * 当定义构造函数，且构造函数中定义了函数，则调用时每new一次，就创建一个新的函数对象，会无意义地重建对象。
			 * 
			 */

			function Person(){
			 	this.name="Zhang"
			 }

			 var obj = new Person()
			 console.log(obj)

			 var obj2 = new Person
			 console.log(obj2)

			 /**
			  * 原型：prototype
			  * 每一个函数天生自带一个属性，叫做prototype，是一个对象
			  * 
			  */
			console.log('prototype: ')
			console.log(Person.prototype)
			Person.prototype.doSomething = function(){ console.log('我是Person原型上的方法')}		
			
			/**
			 * 每一个对象，当它的成员被访问时，如果自己没有这个成员或属性，会自动去所属构造函数的 prototype 去查找
			 * Person中没有定义该方法，调用时，调的是prototype上的方法：
			 */
			 var obj3 = new Person
			 obj3.doSomething()


		</script>
</body>
</html>
```

