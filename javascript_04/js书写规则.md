js书写规则



1. JS代码书写位置：

   - 行内式：

     - a标签：写在href属性上

       ```html
       <a href="javascript:alert('hell');">点我一下</a>
       ```

       

     - 非a标签：书写在行为属性上
     
       ```html
       <div onclick="alert('hell')">点我一下</div>
       ```
       
       
     
   - 内嵌式：

     书写在script标签内,打开页面会直接执行

     ```html
     <script>
     	alert('hell')
     </script>
     ```

     

   - 外链式：

     js代码定义在一个js文件中，html中导入引用，打开页面会直接执行：

     ```html
     <script src="./xxx.js"></script>
     ```
     
     

2. js语法：

   - 基本数据类型：

     1）数据类型：100，-102.341， 2e5, 0x80(16进制),  0o100(8进制), 0b100(2进制)

     2）空类型：null 表示有值，是个空值；undefined表示没有值

     3）检查数据类型：typeof 要检查的变量

     4）一个定义了但未初始化的变量 typeof 是undefined；typeof null 的值是object

   - 数据类型转换：

     1）数值类型转换：

     -  Number(转换内容)，parseInt(转换内容)，parseFloat(转换内容)；

      		其中parseInt转换float类型只能得到整数部分；

     ​		 Number()只能转换类似'12'这样的字符串，而parseInt(‘12we’)得到12。

     -    字符串转换：

        String(转换内容) ，转换内容.toString

     - 布尔值转换：

       Boolean(转换内容)

       **js中，false，0，NaN, ’‘，undefined， null 这5种转换boolean都为false。**

       ```html
       <script>
       	var s1 = 'abc'
           console.log(s1)
           console.log(typeof s1)
           
           var b1 = Boolean(s1)
           console.log(b1)
           console.log(typeof b1)
       </script>
       ```

   - 运算符：

     +： 加号两边是number或者boolean会进行数值运算，只要有一边是string就会字符串拼接运算。

     ==/!=：只比较变量值是否相等，不考虑数据类型，如 8 == ’8‘ 结果是true

     ===/!==: 值和数据类型都相等才是true

     n++/++n: 后置运算符先再与运算再改变n的值，前置运算符先改变n的值再参与运算

     其他运算符跟Java差异不大。

   - 引用数据类型：

     1. 对象object,类似lua中的table类型:

        ```js
        // 声明空对象
        var obj = {}
        // 增加成员
        obj.name = "video"
        obj['tag'] = 'live'
        obj['duration'] = null
        console.log(obj)
     
        // 改
        obj.duration = 2400
        obj['tag'] = "play"
        console.log(obj)
     
        // 删除
        delete obj.name
        delete obj['tag']
        console.log(obj)
        ```

     2. 数组Array:

        ```js
        var arr = [100,102,103,104]
        console.log(arr)
        console.log(arr.length)
        
        // 修改数组长度
        arr.length = 2
        console.log(arr)
        console.log(arr.length)
        ```

        常用方法：

        - `.push()` 追加数据到末尾， 返回追加后的数组和数组的length。

        - `.pop() `删除数组最后一个数据， 返回被删除的数据。

        - `.shift()` 删除数组最前一个数据， 返回被删除的数据。

        - `.unshift(数组)` 在数组最前面追加一段数据， 返回数组最新长度。

        - `.reverse()` 数组反转

        - `.splice(开始索引默认0，个数默认0，要插入的数据默认没有值)`   删除数组若干数据，并选择是否插入新的数据， 返回被删除的数据。

          ```js
          var aar = [12,13,14,15]
          console.log('原：'+aar)
          
          // 默认函数
          var res = aar.splice()
          // 将没有变化
          console.log('得到：'+aar)
          // 将得到空数组
          console.log('得到：'+res)
          
          // 从下标1开始，删除一个元素
          var res = aar.splice(1,1)
          // 将得到[12,14,15]
          console.log('得到：'+aar)
          // 将得到[13]
          console.log('得到：'+res)
          
          // 从下标1开始，删除一个元素,替换为'new'
          var res = aar.splice(1,1,'new')
          // 将得到[12,'new',14,15]
          console.log('得到：'+aar)
          // 将得到[13]
          console.log('得到：'+res)
          ```

          

        - sort()排序,3种：`sort(),  sort(function(a,b){ return a-b}),sort(function(a,b){ return b-a})`。

        - `.join(连接符)`  将数组用连接符转换为一个字符串。

        - `.concat(其他数组)` 拼接两个数组，得到新数组。

        - `.slice(开始索引，结束索引) `左闭右开，截取数组的一段，得到子数组。

        - `.indexOf(元素) `查找所在索引，返回第一次出现的索引。

        - `.forEarch(function(item,index,arr){})` 遍历数组

        - `.map(function(item,index,arr){}) `映射数组,其实就是变换操作

          ```js
          var arr = [10,11,12,13,14]
          console.log(arr)
          
          var res = arr.map(function(item,index,arr){
              return item * 10
          })
          console.log(res)
          ```

        - `.filter(function(item,index,arr){})` 过滤数组

          ```js
          var arr = [10,11,12,13,14]
          console.log(arr)
          
          var res = arr.filter(function(item,index,arr){
              return item % 2 = 0
          })
          console.log(res)
          ```

        - `.every(function(item,index,arr){})` 判断数组每一项是否符合条件

          ```js
          var arr = [10,11,12,13,14]
          console.log(arr)
          
          var res = arr.every(function(item,index,arr){
              return item > 10
          })
          console.log(res)
          ```
          
         - `.some(function(item,index,arr){})` 判断数组至少有一项是否符合条件
        
           ```js
           var arr = [10,11,12,13,14]
           console.log(arr)
                    
           var res = arr.some(function(item,index,arr){
               return item > 10
           })
           console.log(res)
           ```
   
   
   - 字符串操作：
   
     1.  `string.charAt(index)`  获取字符串索引位置的字符。
     
     2. `string.toLowerCase()/toUpperCase()` 转换为小写/大写，返回转换后的字符串。
     
     3. `string.replace(旧内容,新内容) `字符串替换，把第一个旧内容替换为新内容。
     
     4. `string.trim()` 去除首尾空格。
     
     5. `string.split(分隔符)` 分割字符串返回数组。
     
     6. `string.substr(开始索引，截取字符个数)` 截取字符串
     
     7. `string.substring(开始索引，结束索引)`  截取字符串，前闭后开
     
     8. `string.slice(开始索引，结束索引)`  截取字符串，前闭后开
     
   - 数字常用方法：
   
     1. `Math.random()`随机数0~1
   
     2. `Math.round()`四舍五入
   
     3. `Math.ceil()` 向上取整
   
     4. `Math.floor()`向下取整
   
     5. `Math.pow(底数，指数)` 对数字取幂运算
   
     6. `Math.sqrt(数字)` 取二次方根
   
        
   
   - 时间的常用方法：
   
     ​	`var time = new Date()`
     
     1. `time.getFullYear()`  获取年份
     2. `time.getMonth()/.getDate()/.getHours()/.getMinutes() /.getSeconds()/.getDay()` 获取月、日、时、分、秒、星期几
     3. `time.getTime()`  获取时间戳。
     
     

