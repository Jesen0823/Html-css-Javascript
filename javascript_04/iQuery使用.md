### 一、iQuery选择器

1. iQuery选择器语法：`$(xxx)`

   ```html
   <!DOCTYPE html>
   	<head>
   		<meta charset="utf-8">
   		<meta name="viewport" content="width=device-width, initial-scale=1.0">
   		<meta http-equiv="X-UA-Compatible" content="ie=edge">
   		<title>iQuery 初使用</title>
   	</head>
   
   	<body>
   
   		<ul>
   			<li class="cA">1</li>
   			<li>2</li>
   			<li class="cB">3</li>
   			<li class="cB">4</li>
   			<li>5</li>
   			<li id='box'>6</li>
   		</ul>
   		
   		<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
   
   		<script type="text/javascript">
   			console.log($)
   			console.log(jQuery)
   
   			// id选择器
   			console.log($('#box'))
   
   			// 类名选择器
   			console.log($('.cA'))
   
   			// 标签选择器
   			console.log($('li'))
   
   			// 结构选择器
   			console.log($('li:nth-child(odd)')) // 奇数序列
   			console.log($('li:nth-child(even)')) // 偶数序列
   
   		</script>
   	</body>
   </html>
   ```

2.  jQuery选择器的筛选器:

   作用：对选择器的结果进行帅选。常见有：
   
   * first()
   * next()
   * pre()
   * parent()
   * siblings()  拿到该元素所有平级元素或兄弟元素
   * last()
   * nextAll()
   * preAll()
   * parents() 拿到该元素所有父级结构，直到html标签
   * find() 找到该元素所有children中满足选择器要求的元素
   * eq(index)
   * ... ...
   
   ```html
   <!DOCTYPE html>
   	<head>
   		<meta charset="utf-8">
   		<meta name="viewport" content="width=device-width, initial-scale=1.0">
   		<meta http-equiv="X-UA-Compatible" content="ie=edge">
   		<title>iQuery 初使用</title>
   	</head>
   
   	<body>
   
   		<ul>
   			<li class="cA">1</li>
   			<li>2</li>
   			<li class="cB">3</li>
   			<li class="cB">4</li>
   			<li>5</li>
   			<li id='box'>6</li>
   		</ul>
   		
   		<ul id='second'>
   			<li>1</li>
   			<li>2</li>
   			<li>3
   				<i>3子标签</i>
   			</li>
   			<li>4
   				<i>4子标签
   					<p>4孙标签</p>
   				</i>
   			</li>
   			<li>5</li>
   			<span>插入的span</span>
   			<li>6</li>
   			<li>7</li>
   			<li>8</li>
   			<li>9</li>
   			<li>10</li>
   		</ul>
   		<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
   
   		<script type="text/javascript">
   			// 帅选器
   			console.log('筛选器：')
   			console.log($('li').first())
   			console.log($('li').last())
   			console.log($('li').eq(2))
   			console.log($('span').next())
   			console.log($('span').nextAll())
   			console.log($('span').parent())
   			console.log($('.box').parents())
   			console.log($('ul').find('i'))
   
   		</script>
   	</body>
   </html>
   ```
   
   

### 二、jQuery操作文本内容

* html()  // 获取和设置该元素下所有标签与内容，等价原生的 innerHTML

* text()  // 等价原生的innerText

* val()  // 等价于原生的 标签.value

  ```html
  <!DOCTYPE html>
  	<head>
  		<meta charset="utf-8">
  		<meta name="viewport" content="width=device-width, initial-scale=1.0">
  		<meta http-equiv="X-UA-Compatible" content="ie=edge">
  		<title>iQuery 操作文本内容</title>
  	</head>
  
  	<body>
  		<div>
  			Hello
  			<p>你</p>
  			World
  		</div>
  		<br/>
  
  		<li>
  			第二行
  		</li>
  
  		<input type="text" name="inputEdit" value="请输入用户名">
  		
  		<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
  
  		<script type="text/javascript">
  			
  			// 1. html()方法获取内容
  			console.log($('div').html())
  
  			// 2. html()方法设置内容
  			$('div').html('不速之客')
  			$('li').html('<h2>第二行 不速之客</h2>')
  
  			// 3. text()获取内容
  			var content= $('div').text()
  			console.log(content)
  			// 4. text()设置内容
  			$('div').text('text()设置的内容')
  
  			// 5. val()方法的使用
  			let c = $('input').val()
  			console.log('c = '+c)
  			$('input').val('请不要输入用户名')
  		</script>
  	</body>
  </html>
  ```

  

### 三、 jQuery操作类名

* addClass()
* removeClass()
* toggleClass()

```js
// 1. addClass
$('div').addClass('e')
// 2. 删除
$('div').removeClass('a')
// 有则删之，无则加之
$('div').toggleClass('f')
```

### 四、jQuery操作样式

* css()

```html
<!DOCTYPE html>
	<head>
		<meta charset="utf-8">
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<meta http-equiv="X-UA-Compatible" content="ie=edge">
		<title>iQuery 操作元素样式</title>

		<style type="text/css">
			div {
				height: 200px;
				background-color: skyblue;
			}
		</style>
	</head>

	<body>
		<div style="width: 100px;" class="box">操作样式style</div>
		
		<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>

		<script type="text/javascript">
			
			// 操作元素样式 css()
			// 1. 获取元素的行内/非行内样式
			console.log($('div').css('width'))
			console.log($('div').css('background-color'))

			// 2. 设置样式 元素集合.css(样式名，样式值)
			// 当单位是px的时候可以省略单位
			$('div').css('height', '100px')
			$('div').css('width', '300')
			$('div').css('color','#FF0000')
			$('div').css('background-color','purple')

			// 3. 批量设置样式 元素集合.css({对象})
			$('div').css({
				width:260,
				height:120,
				opacity:0.68,
				'color':'pink'
			})

		</script>
	</body>
</html>
```



### 五、jQuery操作元素属性

* attr()/ removeAttr()
* prop() /removeProp()

```html
<!DOCTYPE html>
	<head>
		<meta charset="utf-8">
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<meta http-equiv="X-UA-Compatible" content="ie=edge">
		<title>iQuery 操作元素属性</title>

		<style type="text/css">
			div {
				height: 200px;
				background-color: skyblue;
			}
		</style>
	</head>

	<body>
		<div id="box" myCustom="hello">操作元素属性 div</div>
		
		<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>

		<script type="text/javascript">
			// 操作元素属性

			// 1. attr() 实际应用中一般用来操作自定义属性,非自定义属性也可以； 元素.attr(要获取的属性名)
			var cl = $('div').attr('myCustom')
			console.log(cl)
			console.log($('div').attr('id'))

			// 2. attr()设置；元素.attr(属性名,属性值)
			$('div').attr("add",100)
			$('div').attr("id",'container')

			// 3. removeAttr()
			$('div').removeAttr('add')

			// 4. prop()设置属性： 设置原生属性会加在元素标签中，设置自定义属性会加在元素对象中而不是在标签里
			$('div').prop('id','test')
			$('div').prop('custom2',200)
			console.log($('div'))

			// 5. prop()获取属性，只能获取prop()方法自己设置的属性
			console.log('prop 获取属性：')
			console.log($('div').prop('id'))
			console.log($('div').prop('custom2'))
			console.log($('div').prop('myCustom'))

			// 6. removeProp() 删除属性，只能删除通过prop()方法设置的自定义属性
			$('div').removeProp('custom2')
			
		</script>
	</body>
</html>
```



### 六、iQuery获取元素尺寸

* width()
* height()
* innerWidth()
* innerHeight()
* outerWidth()
* outerHeight()

​     

```html
<!DOCTYPE html>
	<head>
		<meta charset="utf-8">
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<meta http-equiv="X-UA-Compatible" content="ie=edge">
		<title>iQuery 操作元素尺寸</title>

		<style type="text/css">
			* {
				margin: 0;
				padding: 0;
			}

			div {
				width: 300px;
				height: 300px;
				padding: 20px;
				border: 20px solid #333;
				margin: 20px;
				background-color: skyblue;
				background-clip: content-box;
			}
		</style>

	</head>

	<body>
		<div>获取元素尺寸 div</div>
		
		<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>

		<script type="text/javascript">
			// 1. width(),height()方法
			console.log('width: '+$('div').width()) // 300
			console.log('height: '+$('div').height()) // 300

			// 2. innerWidth(), innerHeight()
			console.log('innerwidth: '+$('div').innerWidth()) // 340
			console.log('innerheight: '+$('div').innerHeight()) // 340

			// 3. outerWidth(), outerHeight()
			console.log('outerWidth: '+$('div').outerWidth()) // 380
			console.log('outerHeight: '+$('div').outerHeight()) // 380
			// 包含设置的margin 20
			console.log('outerWidth true: '+$('div').outerWidth(true)) // 420
			console.log('outerHeight true: '+$('div').outerHeight(true)) // 420
			
		</script>
	</body>
</html>
```



### 七、获取元素偏移量

* 元素.offset()  得到对象{top:xx, left:xx}
* 元素.position() 获取定位位置

### 八、jQuery绑定事件

* on()

* one()    // one() 与on()绑定的事件类似，只不过one()绑定事件只能执行一次

* hover()

* 解绑事件：

  * off()
  
    `$('div').off('click')` 解绑click类型的所有函数
  
    `$('div').off('click', handleB)` 解绑click类型的某个触发函数handleB()
  
    `$('div').trigger('click')`  代理触发click事件，不需要鼠标点击
  
  
  
 ### 九、iQuery基本动画 

  1.  显示/隐藏`show(),hide(),toggle` 接收3个参数：

     * 时长
     * 运动曲线
     * 动画完成回调方法

     ```js
     $('div').show(1000,'linear', function (){ console.log('show 完成')})
     $('div').hide(1000,'linear', function (){console.log('hide 完成')})
     
     // 隐藏和显示依次切换
     $('div').toggle(1000,'linear',  function (){console.log('toggle 完成')})
     ```

2. 折叠动画 `slideDown(), slideUp(), slideToggle()` 参数同上

3. 渐隐渐显动画 

   `fadeIn(), fadeOut(), fadeToggle(), fadeTo()`

   > 参数前3个同上
   >
   > fadeTo()四个参数：时长,透明度,运动曲线,结束的回调

​    

```html
<!DOCTYPE html>
	<head>
		<meta charset="utf-8">
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<meta http-equiv="X-UA-Compatible" content="ie=edge">
		<title>iQuery 基本动画</title>

		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}

			div {
				width: 500px;
				height: 500px;
				background-color: deeppink;
			}
		</style>

	</head>

	<body>
		
		<button>show</button>
		<button>hide</button>
		<button>toggle</button>


		<button>slideDown</button>
		<button>slideUp</button>
		<button>slideToggle</button>
		

		<button>fadeIn</button>
		<button>fadeOut</button>
		<button>fadeToggle</button>
		<button>fadeTo</button>

		<div></div>
		
		<!-- <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script> -->
		<script type="text/javascript" src="https://cdn.staticfile.org/jquery/1.11.3/jquery.min.js"></script>

		<script type="text/javascript">
			
			// 显示隐藏动画：
			$('button:nth-child(1)').click(function (){
				$('div').show(1000,'linear', function (){ console.log('show 完成')})
			})

			$('button:nth-child(2)').click(function (){
				$('div').hide(1000,'linear', function (){console.log('hide 完成')})
			})

			$('button:nth-child(3)').click(function (){
				$('div').toggle(1000,'linear',  function (){console.log('toggle 完成')})
			})


			// 折叠动画：
			$('button:nth-child(4)').click(function (){
				$('div').slideDown(1000,'linear', function (){ console.log('slideDown 完成')})
			})

			$('button:nth-child(5)').click(function (){
				$('div').slideUp(1000,'linear', function (){console.log('slideUp 完成')})
			})

			$('button:nth-child(6)').click(function (){
				$('div').slideToggle(1000,'linear',  function (){console.log('slideToggle 完成')})
			})

			// 渐隐渐显动画：
			$('button:nth-child(7)').click(function (){
				$('div').fadeIn(2000,'linear', function (){ console.log('slideDown 完成')})
			})

			$('button:nth-child(8)').click(function (){
				$('div').fadeOut(2000,'linear', function (){console.log('slideUp 完成')})
			})

			$('button:nth-child(9)').click(function (){
				$('div').fadeToggle(2000,'linear',  function (){console.log('slideToggle 完成')})
			})

			$('button:nth-child(10)').click(function (){
				$('div').fadeTo(2000, 0.45, 'linear', function (){console.log('slideToggle 完成')})
			})
		</script>
	</body>
</html>
```

4. 综合函数：

   `animato()`

   接收4个参数：

   -  运动的样式，以一个对象传递
   - 时长
   - 运动曲线
   - 结束回调方法

   **但是：关于颜色和transform的样式是不能运动的**

   ```js
   $('div').animate({
   					width: 600,
   					height:200,
   					'border-radius':'50%'
   				}, 1500,'linear', function (){ console.log(' 完成')})
   ```

5. 动画的结束：

   `stop(), finish()`

   