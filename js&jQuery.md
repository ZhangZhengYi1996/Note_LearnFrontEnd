#   js变量、作用域

### js变量基础复习

- 数据 一次使用 多次使用—— 变量（保存数据的容器）
- 命名：$ _ abd 123 数字不能开头
  - 关键字 保留字

- 声明

### 变量

#### 数据类型和堆栈

- 基本类型（数字，字符串，Boolean，undefined，null） 不可修改
- 引用类型（[array],{object}）可修改
- 堆栈
  - 栈内存  有序排列 大小固定 公寓
    - 保存基本类型 （按值访问）
    - 保存对象地址 —— 引用堆内存中的对象的数据 （按引用访问）
  - 堆内存  空间大小不固定 别墅 可以扩建
    - 引用类型

#### 变量比较和值的复制

- 引用类型比较 
  - 地址不一样 两个不同的引用
- 引用类型复制
  - 浅拷贝 深拷贝 
  - jQuery.extend()

#### 参数传递和类型检测

- 参数传递只有按值一种

- 引用类型 按值（地址）
- 检测类型
  - typeof  数组 对象 null 都是object
  - 引用类型 [] instanceof  object

### 作用域与解析机制

#### 全局作用域和局部作用域

- 变量的作用域 变量起作用的区域或范围
  - 变量的生命周期
  - 哪里访问到
- 局部：函数作用域
  - 没有块级作用域{}

#### 变量对象和作用域链

- 从里层往外层查找

#### js解析机制

- 预先解析
  - 变量=undefined
  - function
- 逐行解读

### 内存管理与垃圾收集机制

- 垃圾收集：释放无用的数据，回收内存
  - 自动 手动
  - 原理：找出没用的，打上标记，释放内存
  - 周期性执行
  - 标记清除——环境中的变量     引用计数
- 解除：null

# js函数

### 面向对象

- var cat={...}
- var cat=new Object()
- Object.create()
- 删除属性 delete cat.name
- "name" in cat 对象中是否有name这个属性
- 遍历属性 for(var p in cat){ cat[p]}  

### 函数

- 一次定义 四处调用
- 命名函数 匿名函数
- 可以添加属性和方法
- 作为数据值使用 堆内存 用变量访问 
- 作为参数
  - ` setTimeout(fn,1000);finction fn(){};` 
  - fn 作为参数使用 访问函数本体 ==不能加括号==
- 作为返回值 
  - fn()();

### 函数定义

- 字面量 
  - function声明
  - var赋值；
- 构造 var add=new Function（"num1","num2"，"return"）字符串；
- 重要区别
  - 预解析 声明 无关顺序

#### 函数定义的位置

- 全局作用域 哪里都能找到
- 函数作用域 在函数内部能找到
- if/for 中定义 不正确 if/for 不是作用域
  -  可以用赋值
- 对象中

### 函数调用

#### 普通函数调用

- 命名函数 name();

- 匿名函数 

  - 赋值给一个变量 name();
  - 直接调用 var name= function（){}==()==; 要避免 function 开头，自我执行  
  - （function（){}）（）；

- 递归调用 在函数内部调用函数本身

  ``` 递归调用
  function factorial(num){
  return num*factorial(num-1);
  }
  ```

#### 方法调用

- operation.add();
- document.onclik(); 浏览器自动调用方法 时间模拟
- operation['@'] 非法字符的方法调用 不能用点   
  - ==当属性是变量 要用【】 不能用点==
- 链式调用 对象属性中return this

#### 构造函数调用

- new add(); 返回一个新对象
- Object(), Array()

#### 间接调用

- add.call (指向的值，1，2，3)
- add.apply（同上，[1,2]）

### 参数使用

- 参数类型 形参&实参
- 参数个数
  - 形参和实参个数一样
  - 实参<形参   当形参可选
  - 实参>形参    形参不写 用arguments
- 参数可以是数组，对象，函数

#### arguments

- 类数组 对象 
- 每一个函数中独有
- 属性 callee 指代函数本身 严格模式下不能用
  - 用 var name=function fn(){}
- 形参个数 fn.length

### 函数的返回值

- return 结束/将值返回

- continue 跳出本次循环

- break 跳出整个 循环

- 返回值 

  - return [a,b,c];数组
- return {};对象  花括号不能换行
  - 函数

# 面向对象

### 对象概述

- 基于原型
  - 依靠构造器 constructor 利用原型 prototype构造出
- 属性：事物的特性
- 方法：事物的功能
- 对象：事物的一个实例 众多人中的一个人
  - 函数对象  new Fun
  - 普通对象
- 原型：利用原型 prototype构造出属性和方法
  - 所有函数都有f.prototype属性  ——》内存地址——》存储着一个对象
  - 每一个函数都是一个对象
  - 构造函数对象：用函数构造器创建函数对象

#### 闭包

- 闭包：拥有许多变量和绑定了这些变量的环境表达式（通常是一个函数）
- 全局变量在函数内部可以访问，但是外边访问不到函数里的局部变量
- ——>在函数a里再定义一个函数b， b嵌套在a里，a需要返回b
- 用途
  - 读取函数内部变量
  - 让变量的值保留在内存中
- 优点
  - 有利于封装 可以访问局部变量
- 缺点
  - 内存占用浪费严重 内存泄漏

### 对象声明方式

- var obj={}

- var obj=new Object();

- 构造函数

  ```javascript
  function person(name,age){
  	this.name=name;//this 当前对象  函数内部只能用this访问
  	this.age=age
  	this.show=function(){
      ...
  	}
  }
  var obj=new person("zs",12); //实例化
  ```

  - 不会显示创建对象 不需要return  属性赋给this

- 工厂方式

  ```javascript
  function creantObject(name,age){
      var obj=new Object();
      obj.name=name;
      obj.age=age;
      obj.run=function (){// 在obj对象中调用属性，用this
          return this.name;
      };
      return obj;
  }
  
  var box=creatObject("zs",18);
  ```

  - 内部创建object 并返回  属性赋给object

- js原型模式

  ```javascript
  function test(){}
  test.prototype.name="";
  ...
  test.prototype.show=function(){};
  
  var obj=new test();
  
  
  //也可以这么写
  test.prototype={
  ...
  }
  var obj=new test();
  ```

  - 利用prototype prototype是object子对象

- 混合模式 构造+原型

  ```javascript
  functioon test(name,age){
  this.name=name;
  this.age=age;
  }
  test.prototype={
  show:function(){}
  }
  var obj=new test("zs",12);
  ```

  - 常用

### 对象遍历及存储

- 遍历

  - 可以当作数组处理  for in

  - var i in obj  i是方法或属性

- 存储

  - 两个对象是完全独立的

### 封装

- encapsulation 把对象内部数据和操作细节进行隐藏
- 闭包——》特权方法

### 继承

#### 原型和原型链

- 原型链：js在创建对象的时候，有一个 __ proto __ 的内置属性，用于指向创建它的函数对象的原型对象prototype
- p.__ proto__=person.prototype
- 原型继承：用到原型链的概念

#### 构造函数继承

- 在子类内部构造父类的对象实现继承
- call(),apply()
- parent.call(this,... )

### 关键词

- instanceof 变量是否是对象的实例
- delete 删除对象属性  （方法不行） 不能删除原型链中的的属性和变量
- call apply  第一个参数改变this的指向
- arguments.callee 在函数内部调用本函数
- callee 返回正在执行的function对象
- this 
  - 可以在函数内部定义属性/变量   //全局变量
  - 作为方法调用 构造函数内 this表示当前对象
  - call apply 

### 冒充

- 将父类的属性和方法传给子类，作为特权属性和方法
-  用prototype定义的属性和方法，是共有的，子类无法继承

# 正则表达式

- 用模式和字符串匹配
- 普通字符&特殊字符
- 字面量var pattern=/js123_汉字,;!@/  或者 构造 new RegExp("js")
  - ==构造函数里有转义字符，要双重转义 如\\s, 需要再加一个\\==

#### 让正则匹配字符

```javascript
var str="i love js";
var pattern=/js/;
pattern.test(str);//找到返回true
pattern.exec(str);//找到返回字符串，找不到返回null
```

- 默认区分大小写

- 模式修饰符

  - i  ignoreCase 忽视大小写
  - g global 全局
  - m multiline 行首行尾

- ```javascript
  var pattern=/js/ig;//不分大小写，全局匹配
  var pattern=new RegExp("js","i");
  ```

#### 使用何种方式创建

- 构造可以使用变量

#### 简单转义字符

- 将特殊字符转成普通字符  用反斜杠\   反斜杠在字符串中，本身就需要转义 
- 特殊字符
  - \ /
- 也可以将普通字符转成特殊字符 如\n 换行
  - \n \t \x0A(\n) 
  - unicode 编码    匹配汉字  范围\u4e00-\u9fa5

#### 字符类

- 【abcdeffgg】匹配任意一个字符  先匹配到谁就是谁
- 【^ js】取反 除了js的任意一个字符
- 【a-zA-Z0-9@_】表示范围  保证前面小于等于后面的值
- 匹配汉字  【\u4e00-\u9fa5】

#### 常用字符类

- /./  匹配除了\n
-  /\w/  表示【a-zA-Z0-9_】
- /\W/ 大写是小写取反
- /\d/  表示0-9   \D
- /\s/  表示空格或制表符    \S

#### 重复

- 匹配3次 \d{3}
- 还可以是范围{1,2}  1-2个
- 至少一个 {1,}——>+
- {0,1}——>  ?
- {0,}——>*

#### 非贪婪的重复

- 默认 尽可能多匹配
- 量词后面再加一个问号
  - 有条件 ：正则总是寻找第一个可能匹配的关键字

#### 选择 分组 引用

- 选择 /a|b|c/  a或b或c
- /(ab)c/ 分组 返回abc，ab
  - （？：ab）不返回括号中的内容
- 可以嵌套 (a(b(c)))
- (ab cd ab)   /(ab) cd \1/
  - \1表示和第一个分组一样的内容 

### 位置匹配

#### 首尾匹配

- /^js$/  ^ 首 \$ 尾
- /^\d+$/ 从开头到结尾全是数字

#### 单词边界匹配

- /\bjs/ \b表示边界
- class="one two three"
  - 要匹配two  /\btwo\b/

#### 单词前瞻性匹配和负向前瞻性匹配

- 前瞻性

  ```js
  var str="javascript";
  //java后面是script才匹配java
  var pattern = /java(?=script)/;
  ```

- 负向前瞻性

  ```js
  var str="javascript";
  //java后面是script 不匹配java
  var pattern = /java(?!script)/;
  ```

### RegExp对象

#### 实例方法

- new RegExp("js")    可以传变量
- ==构造函数里有转义字符，要双重转义 如\\s, 需要再加一个\\==

- ("\\\\") 四个反斜杠  匹配一个反斜杠

- exec()  从第0个位置开始匹配 找到一个就结束 有index属性

  - g 全局匹配 找出所有

  - pattern.lastIndex  非全局匹配时，为0，不会变化；全局匹配时，每一次执行过后就会发生变化，为匹配上的字符的下一个位置；全部匹配完之后，自动重新置为0

  - ```js
    var str="1.js 2.js 3.js";
    var pattern=/js/g;
    var total=0,match="",result;
    while((result=pattern.exec(str))!=null){
    //匹配到全部的pattern
        total++;
        match+="第"+total+"个找到的是："+result[0]+"，它的位置是："+result.index+"\n";
    }
    match+="共找到"+total+"个js";
    console.log(str);
    console.log(match);
    ```

- test()
  
  - test.lastIndex 

- pattern.toString()
- pattern.toLocaleString()
- pattern.valueOf()  //返回正则本身

#### 实例属性

- pattern.ignoreCase  //是否有i
- pattern.global  //是否有g
- pattern.multiline  //是否有m

- pattern.source 返回字面量本身

- pattern.lastIndex

#### 构造函数属性(不常用)

- RegExp.input  要先调用exec或者test 属性才会有值
- input  ——>   .$_    ["\$_"]   用.表示的可以用[]
- .lastMatch 最近一次匹配的字符    ['$&']
- leftContext  上一次匹配左边剩余字符   ["$`"]   right["\$'"]
- lastParen   括号里的 [$+]  

- 分组 \$1~\$9

### string对象中与正则相关的方法

- str.search(pattern)  返回位置，没找到返回-1
- str.match(pattern)    类似exec
  - 不同点：全局匹配，一次性找全，但不返回分组中内容

- /js$/mg  多行全局尾匹配  能找到每一行结尾的js

- str.split() 字符串变成数组
- str.replace("a","b") 把a换成b
  - 分组要用$1

### 常用的正则表达式

- qq
  
  - /^[1-9]\d{4,}$/
  
- 昵称 2-18位 中英文 下划线 数字
  
  - /^[\u4e00-\u9fa5\w]{2,18}$/
  
- 密码 6-16位 区分大小写 不能有空格
  
  - /^\S{6,16}$/
  
- 去除字符串首尾的空白字符

  - pattern=/^\s+|\s+$/g

  - str.replace(pattern,"");

  - 也可以把首尾分开，用2个正则，str.repalce(pattern1,"").repalce(pattern2,"");

  - ```js
    function trim(str){
        return str.repalce(/^\s+/,"").replace(/\s+$/,"");
    }
    ```

- 转驼峰

  - 如background-color      js:backgroundColor

  - ```js
    var pattern=/-([a-z])/ig
    str.replace(pattern,function(all,letter){
        return letter.toUpperCase();
    });
    
    function toCamelCase(str){
      return str.replace(pattern,function(all,letter){
        return letter.toUpperCase();
    })  
    }
    ```

- 匹配html标签

  - /<\/?[a-zA-Z]+(\s+[a-zA-Z+=".*")\*>/g
  - /<[\^>]+>/g
  
- email

  - /(?:\w+\\.)*\w+@(?:\w+\\.)+[a-z]/i
  - /^[a-z0-9]+(?:\[.-\_][a-z0-9]+)*@[a-z0-9]+(?:\[.-\_][a-z0-9]+)\*\\.[a-z]{2,4}$/i

- url

  - (协议://)主机名(:端口号)(/路径)
  - /\^(https?:\/\/)?([\^:\/]+)(:\d+)?(\/.*)?$/
  - 匹配主机名
    - /^([a-z0-9]\\.|[a-z0-9] [-a-z0-9]*[a-z0-9]\\.)\*([a-z]+)$/i

### 表单验证

#### h5验证

- 不够灵活 还是存在一些问题

#### js验证

