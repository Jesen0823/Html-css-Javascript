### 一、BOM操作

BOM - 操作浏览器相关的属性和方法

1. 获取浏览器窗口尺寸

   `window.innerWidth/window.innerHeight `  获取浏览器窗口宽度、高度

2. 浏览器的弹出层

   * 提示框： `window.alert('提示信息')`
   * 询问框： `window.confirm('是否确保周围环境安全？') `返回boolean类型。
   * 输入框： `window.prompt('请输入信息')`， 返回输入内容，如果取消就返回null。

3. 开启和关闭标签页：

   * 开启： `window.open('地址')`
   * 关闭：`window.close()`

4. 浏览器常见事件：

   * 资源加载完毕： `window.onload = function(){}`
   * 可视尺寸改变：`window.onresize = function(){}`
   * 滚动条位置改变：`window.onscroll = function(){}`

5. 浏览器历史记录操作：

   * 回退页面： `window.history.back()`

   * 前进页面：`window.history.forward()`

   * 浏览器卷去的高度： `var height = document.documentElement.scrollTop || document.body.scrollTop`

   * 滚动条滚动到： 

     ```html
     <!DOCTYPE html>
     <html>
     <head>
     	<meta charset="utf-8">
     	<title>浏览器滚动条 滚动到指定位置</title>
     	<style type="text/css">
     		body{width: 3000px; height: 3000px;}
     		button{position: fixed; bottom: 50px; right: 50px;}
     	</style>
     </head>
     <body>
     
     	<button id ='go'>开始</button>
     
     	<script>
     		go.onclick = function(){
     			window.scrollTo({
     				left:300,
     				top:400,
     				behavior:'smooth'
     			})
     		}
     	</script>
     </body>
     </html>
     ```



### 二、定时器

1. 周期定时器：`setInterval(函数，时间)`

   ```js
   var timer1 = setInterval(function(){
       console.log('定时器执行一次')
   },1000)
   ```

   

2. 延迟定时器：`setTimeout(函数，时间)`

   ```js
   var timer2 = setTimeout(function(){
       console.log('定时器执行时间到了')
   },3000)
   ```

3. 关闭定时器：

   ```
   clearInterval(timer1)
   clearTimeout(timer1)
   // 两种效果一样
   ```



### 三、DOM用法

​	DOM即操作页面元素的位置、样式、事件处理等。

1. 获取元素

   * 根据id获取  `document.getElementById('id名称')`
   * 根据元素类名获取  `document.getElementsByClassName('元素类名')`
   * 根据元素标签名获取 `document.getElementsByTagName('标签名')`
   * 根据选择器获取一个 `document.querySelector('选择器')` ，获取文档流中第一个满足选择器规则的元素
   * 根据选择器获取一组 `document.querySelectorAll('选择器')`

   ```html
   <!DOCTYPE html>
   <html>
   <head>
   	<meta charset="utf-8">
   	<title>DOM的使用</title>
   </head>
   <body>
   	<div>一号</div>
   	<div class="box">二号</div>
   	<div class="box content">二号内容</div>
   	<div class="box" id="container">三号</div>
   	<p>一个段落</p>
   	<p id="testText">两个段落</p>
   
   	<script type="text/javascript">
   		var ele = document.getElementById('“container')
   		console.log('get element by id: </br>')
   		console.log(ele)
   
   		var ele2 = document.getElementsByClassName("box")
   		console.log(ele2)
   		var ele3 = document.getElementsByClassName("content")
   		console.log(ele3)
   
   
   		var ele4 = document.getElementsByTagName('p')
   		console.log('根据标签名获取到的元素：')
   		console.log(ele4)
   
   		var ele5 = document.querySelector('div')
   		console.log('根据选择器获取到的元素，只选第一个：')
   		console.log(ele5)
   		var ele6 = document.querySelector('.box')
   		console.log('根据选择器获取到的元素，只选第一个：')
   		console.log(ele6)
   
   		var ele7 = document.querySelectorAll('.box')
   		console.log('根据选择器获取到的元素，返回所有符合条件：')
   		console.log(ele7)
   	</script>
   </body>
   </html>
   ```

   

2. 操作元素内容：

   * 操作元素文本内容：`ele.innerText = '新内容'`
   * 操作元素的超文本内容：`ele.innerHTML = '新内容'`
   * 操作元素原生属性： `ele.属性 = '属性值'`
   * 操作元素的自定义属性：
     * 获取属性：`元素.getAttribute('属性名')`
     * 设置属性：`元素.setAttribute('属性名'，'属性值')`
     * 删除属性：`元素.removeAttribute('属性名')`
   * 操作元素类名：`元素.className='newName'`
   * 操作元素行内样式：`元素.style.样式名='样式值'`
   * 获取元素的非行内样式：`window.getComputedStyle(元素).样式名`  即可获取行内样式又可获取非行内样式

   ```html
   <!DOCTYPE html>
   <html>
   <head>
   	<meta charset="utf-8">
   	<title>DOM的使用</title>
   </head>
   <body>
   	<div>一号</div>
   	<div class="box">二号</div>
   	<div class="box content" style="width: 200px;height: 100px;background-color: pink;">二号内容</div>
   	<div class="box" id="container">三号</div>
   	<p>一个段落</p>
   	<p id="testText">两个段落</p>
   	<input type="password" custom='自定义属性' name="">
   	<button>操作元素内容</button>
   	<button>操作元素超文本</button>
   	<button>操作元素属性</button>
   	<button>操作元素的自定义属性</button>
   	<button>修改元素行内样式</button>
   	<script type="text/javascript">
   		var ele = document.getElementById('“container')
   		console.log('get element by id: </br>')
   		console.log(ele)
   
   		var ele2 = document.getElementsByClassName("box")
   		console.log(ele2)
   		var ele3 = document.getElementsByClassName("content")
   		console.log(ele3)
   
   
   		var ele4 = document.getElementsByTagName('p')
   		console.log('根据标签名获取到的元素：')
   		console.log(ele4)
   
   		var ele5 = document.querySelector('div')
   		console.log('根据选择器获取到的元素，只选第一个：')
   		console.log(ele5)
   		var ele6 = document.querySelector('.box')
   		console.log('根据选择器获取到的元素，只选第一个：')
   		console.log(ele6)
   
   		var ele7 = document.querySelectorAll('.box')
   		console.log('根据选择器获取到的元素，返回所有符合条件：')
   		console.log(ele7)
   
   		/* 操作元素内容 */
   		var eleP = document.getElementById('testText')
   		var btn = document.querySelectorAll('button')[0]
   		console.log('元素初始文本内容：')
   		console.log(eleP.innerText)
   		btn.onclick = function(){
   			// 修改文本内容
   			eleP.innerText = '修改为此内容'
   		}
   		var btn2 = document.querySelectorAll('button')[1]
   		console.log('元素初始超文本内容：')
   		console.log(eleP.innerHTML)
   		btn2.onclick = function(){
   			// 修改超文本内容
   			eleP.innerHTML = '<span>修改了超文本</span>'
   		}
   
   		var input = document.querySelector('input')
   		var btn3 = document.querySelectorAll('button')[2]
   		console.log('input元素初始type：')
   		console.log(input.type)
   		btn3.onclick = function(){
   			// 修改超文本内容
   			input.type = 'checkbox'
   			eleP.color = '#FF0000'
   		}
   
   		var btn4 = document.querySelectorAll('button')[3]
   		var res = input.getAttribute('custom')
   		console.log('input元素初始自定义属性：')
   		console.log(input.res)
   		btn4.onclick = function(){
   			// 修改自定义属性
   			input.setAttribute('custom','自定义属性被修改了')
   		}
   
   		var btn5 = document.querySelectorAll('button')[4]
   		var div3 = document.querySelectorAll('div')[2]
   		btn5.onclick = function(){
   			// 修改元素样式
   			div3.style.width = '120px'
   			div3.style.height= '500px'
   			div3.style.backgroundColor = 'skyblue'
   			
   		}
   	</script>
   </body>
   </html>
   ```