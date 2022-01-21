## ES6的新特性



### 一、定义变量

1.  旧版本：定义变量用 var

2. ES6新增：let 定义变量，const 定义常量

3. 区别：

   * var会与解析；var 可以声明两个重名的变量；var没有块级作用域。

   * let/const不会与解析；不能定义重名变量；有块级作用域

   * let定义变量时可以先不赋初值，var 定义时需要赋值初始化，const也是需要初始化。

     ```js
     /* 1. 预解析： */
     
     			// 1.1 正常执行
     			console.log(num)
     			var num = 100
     			console.log(num)
     
     			// 1.2 不能在定义变量之前使用变量，第一行报错
     			console.log(num2)
     			let num2 = 200
     			console.log(num2)		
     
     			/* 2. 重复变量： */	
     
     			// 2.1 正常运行
     			var a = 30
     			var a = 31
     			console.log(a)
     
     			// 2.2 错误 不允许声明重复变量名的变量
     			let b = 32
     			let b = 33
     			console.log(b)
     
     			/* 3. 块级作用域，大括号包裹的区域： */
     
     			// 3.1 OK运行
     			if(true){
     				var n = 80
     				console.log('块内 n：'+n)
     			}
     			console.log('块外 n：'+n)
     
     			// 3.2
     			if(true){
     				let m = 90
     				console.log('块内 m：'+m)
     			}
     			// 不允许
     			console.log('块外 m：'+m)
     ```

     

### 二、箭头函数

```js
var fun1 = function{ console.log('I am fun1')}

// 箭头函数
var fun2 = () =>{ console.log('I am fun2')}
```

1. 箭头函数的特点：

   * 当函数形参**只有一个**的时候，（）可以省略

     ```js
     var fun3 = function(param){ console.log('一个形参：'+param)}
     
     var fun3 = (param) => { console.log('一个形参 箭头：'+param)}
     
     var fun3 = param => { console.log('一个形参 无() 箭头：'+param)}
     ```

   * 函数体只有一行时，箭头函数的大括号可以省略，默认返回一行的执行结果
   
     ```js
     var fun4 = param => console.log('fun 4 省略{}')
     ```
   
   * 普通函数中有内部默认参数 arguments,箭头函数中没有
   
   * 箭头函数内没有 this
   
     ```js
     var obj = {
         fun1: function(){ console.log(this) }
         fun2:()=> { console.log(this)}
     }
     
     obj.fun1()
     obj.fun2()
     ```
   
     

### 三、ES6 的函数默认值

```js
function fun(a = 10, b = 11){
    console.log('a='+a+', b='+b)
}

console.log(fun(2))
```

### 四、ES6的解构赋值

1. 解构赋值可以快速从对象或数组中获取成员。

2. 解构赋值分两种：

   * 数组的解构赋值

     ```js
     let arr = ['G','P','K']
     let a = arr[0]
     let b = arr[1]
     let c = arr[2]
     
     // 解构赋值
     let [e1, e2, e3] = ['G','P','K']
     console.log(e1)
     ```

     

   * 对象的解构赋值

     ```js
     // 普通用法：
     let obj = {
         name:'apple'
         col:'red'
     }
     let name = obj.name
     let color = obj.col
     
     // 解构赋值：
     let obj2 = {
         name2:'apple2'
         col2:'red2'
     }
     
     // 等价于 let name = obj.name
     var {name2, col2} = obj
     // 也可以起别名：
     var {name2:n1} = obj
     console.log('别名n1= '+n1)
     ```

   ### 五、ES6字符串

   在ES6提供了除`''`  `""` 以外的样式，即 ``,类似kotlin中的用法可以往字符串传参：

   ```js
   var num = 86
   var str = `我有${num}种方式解决它`
   console.log('str = '+str)
   ```



### 	六、展开运算符...

​       作用：展开数组的[]或者展开对象的{}，拿到一串内容序列。

​		**用途：**

   1. 数组合并：

      ```js
      var arr1 = [1,2,3]
      var arr2 = [4,5]
      var arr3 = [6,7,8,9]
      var all = [...arr1, ...arr2, ...arr3]
      console.log(all)
      ```

   2. 函数传参：

      ```js
      var arrP = [1,13,5,7]
      function maxValue(a){ return Math.max(...a)}
      let ret = maxValue(arrP)
      console.log(ret)
      ```

3. 复制对象:

   -<u>**注意：有相同属性的时候，...obj的顺序，后面的相同属性会覆盖前面的**</u>,

   比如下面的name属性：-

   ```js
   var obj = {
       time:2019,
       sole:200,
       name:'pole'
   }
   var objAll = {
       total:1000,
       ...obj,
       name:'ketol'
   }
   console.log(objAll)
   ```

   ### 七、ES6的类语法

   ```js
   /** 1. 旧的类和构造函数：*/
   			function Phone(name,brand, screenSize){
   				this.name = name
   				this.brand = brand
   				this.screenSize = screenSize
   			}
   
   			// 1.1 原型的方法
   			Phone.prototype.test = function(){ console.log(`手机 ${this.name}正常开机`)}
   
   			// 1.2 定义类构造的静态变量和静态属性
   			Phone.year = 3
   			Phone.isFixFree = function(){
   				return '在保修期内'
   			}
   			// 定义构造方法完成
   
   			var myPhone = new Phone('iphone-6s','apple',5200)
   			console.log(myPhone)
   			myPhone.test()
   
   			// 1.3 必须用new的地方没有用new，也不会报错，但是调用无效
   			var yourPhone = Phone('HUAWEI-10','huawei',4800)
   			console.log(yourPhone)
   
   			// 调用静态属性和方法
   			console.log('保修期：'+Phone.year)
   			console.log('是否保修期内：'+Phone.isFixFree())
   
   			/** 2. ES6 类和构造函数：*/
   			class SmartPhone{
   				// 2.1 构造函数
   				constructor (name,brand, screenSize){
   					this.name = name
   					this.brand = brand
   					this.screenSize = screenSize
   				}
   
   				test2(){
   					console.log(`手机 ${this.name}正常开机`)
   				}
   
   				// 2.2 静态变量和函数
   				static yearS = 2
   				static isFixFreeS (){
   					return '在保修期内'
   				}
   			}
   
   			// 2.3 使用
   			var mySPhone = new SmartPhone('iphone-6s','apple',5200)
   			console.log(mySPhone)
   			mySPhone.test2()
   
   			// 2.4 必须用new的地方没有用new，会报错
   			//var yourSPhone = SmartPhone('HUAWEI-10','huawei',4800)
   			//console.log(yourSPhone)
   
   			// 2.5 调用静态属性和方法
   			console.log('保修期：'+SmartPhone.yearS)
   			console.log('是否保修期内：'+SmartPhone.isFixFreeS())
   ```

   