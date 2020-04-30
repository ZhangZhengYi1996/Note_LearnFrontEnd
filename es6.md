### let和const

#### let与块级作用域

- 不声明变量直接使用，就会变成window.xxx，会对window对象造成污染
- let只在当前块级作用域内有效
- 不能重复声明
- 不存在变量提升  执行上下文
- 暂存死区，向上的作用域存在同名变量也是取不到的
- 循环绑定点击事件，可以用let，循环一次就生成一个块级作用域

#### const

- 常量声明，必须赋值
- 不可变
- 引用类型的常量可以被修改？
  - 对象里面的属性可以改变，数组同理
  - 实际的引用地址并不能变

- 如何防止引用类型的常量被修改？

  - object.freeze()

- es6之前怎么声明常量？

  - Object.defineProperty(object,属性名，属性值)

  - writeable：false

  - object.seal(obj)  防止对象被扩展，但是可以修改值

  - ```javascript
    Object.defineProperty(Object,"freezeFill",{
        value:function(obj){
            for(let i in obj){
                if(obj[i] instanceof Object){Object.freezeFill(obj[i])}
                if(obj.hasOwnProperty(i)){
                  Object.defineProperty(obj,i,{
                      writable:false,
                  });
                }
            }
            Object.seal(obj);
        }
    })
    ```

### es6变量的解构赋值

#### 数组

```javascript
let arr=[1,2,3];
let [a,b,c]=arr;
let [ , ,d]=arr;
```

- 扩展运算符...
  - 展开数组
  - [a,...c]=arr  剩下的作为一个数组给c
- 默认值
  - 匹配不到时就赋值undefined
  - 只有当值为undefined时，如果设置了默认值，值就是默认值
  - null依旧是null
- 交换变量
  - [a,b]=[b,a]
- 接受多个函数返回值

#### 对象

- 属性名必须一致才能匹配，与顺序无关
  - const{key}=obj
  - const{a:[b]}=obj 取到属性a的第一项，a的值是一个数组
  - {one:[{a},{a:b}]}  取第二个a的时候，要把值赋给新的变量b，解决了有两个重名的a这个问题
- 结合扩展运算符
  - {a,...b} 把剩下的作为一个对象给b
  - 对象合并 obj2={a：1，...obj2}
- 对已经声明的变量进行对象的解构赋值
  - ({age}=obj)
- 默认值，与数组相似
- 提取对象属性
- 适用对象传入乱序的函数参数
  - function({one,two,three=3}){} 传入一个对象，并且可以有默认值
- 获取多个 函数返回值

#### 字符串

- [a,b,...c]=str ..c是剩下的字符组成的数组
- 可以提取length，split

#### 数值与布尔值

- {valueOf}=1是可以取到的 生成一个包装对象

#### 函数参数

- 参数可以传入数组或对象，进行解构赋值，调用是对传入的对象进行解析

### es6扩展

#### 字符串

- 字符串模板
  - \`str${变量}str\`,不需要加号，可以嵌套，还可以后接字符串的各种方法，还可以调用函数
- 新方法
  - padStart padEnd(位数，str)  补足字符串到相应长度
  - repeat(多少遍) 复制字符串
  - startsWith endsWith(str) 以什么开头什么结尾
  - includes  和indexOf差不多 判断是否存在子串
- for of遍历字符串
  - for循环
  - 转成数组forEach
- unicode表示法
  - codePointAt(0).toString(16) 获取码点
  - at 根据下标去字符

#### 正则

- 修饰符
  - /reg/u.test(str)  //识别unicode字符
  - y 粘连修饰符 一定要连续的才能匹配到多个

#### 数值

- 进制表示法
  - 八进制 0o
  - 二进制0b
- 新的方法
  - Number.parseInt ,Number.parseFloat, Number.isNaN ,Number.isFinite, 
  - Number.isSafeInteger() 数字是否在js可以精确表示的范围之
    - 2^53-1
    - Number.MAX_SAFE_INTERGER
  - 幂运算 2**10  =1024 ，如果有多个幂运算，从右开始运算

#### 函数

- 默认参数，传参数的时候可以直接赋值当成默认参数，可以是表达式

  - （a, b=10+a)

- 结合扩展运算符（剩余参数）

  - 剩下的参数聚合变成一个数组传入函数

- 箭头函数

  - const add = (a,b) =>a+b;  会return a+b，有返回值

  - const add = (a,b) =>{

    其他操作，多行

    return a+b

    };

  - const add = (a,b) => vois a+b，可以避免返回值

  - 没有arguments对象

  - 没有自己的this，它的this指向定义函数所处的环境

#### 对象

- 简洁表示法
  - 方法名（）{},省略function
  - name：name可以直接写成name
- 属性名表达式
  - 复杂的属性名可以通过中括号[ ]访问
  - 定义对象的属性的时候，属性名也可以用[ 里面可以是变量或者表达式]
- 扩展运算符------复制对象
  - cobj=[...obj]   是浅拷贝
- 扩展运算符------合并对象
- 新方法
  - Object.is   === 类似全等，但有如下差别
    - +0 -0   false
    - NaN  NaN  true 
  - Object.assign 合并对象 也是浅拷贝
  - Object.keys  配合for of 循环
  - Object.values
  - Object.entries
  - \_\_proto\_\_ 当前对象的原型
  - Object.setPrototypeOf（a,b） 修改a对象的原型为b
  - Object.getPrototypeOf（obj) ===obj.\_\_proto\_\_
  - super 关键字 可以访问到对象的原型，super.name,方法一定要用对象的简介表示法

#### 数组

- 扩展运算符
  - 数组解构
  - 函数传参的时候可以用[...arr]将参数展开成每一项，类似apply
  - 合并数组
  - 复制数组
  - 配合生成器函数，接受返回结果变成数组
  - 将集合变成数组
- 新方法
  - Array.from（obj，callback） 可以将一个类数组转为数组
    - Array.prototype.slice.call()也可以把类数组转为数组
    - [...arguments]
  - Array.of(a,b,c) 合成数组
  - arr.fill（num，start，end） 填充覆盖   
  - Array.includes  是否有某一项
  - keys
  - values
  - entries
  - find(value,index,arr) 根据callback按顺序遍历数组，当返回true，就返回当前遍历到的值
  - findIndex  返回下标index

### Promise

- promise对象用于表示一个异步操作的最终状态（完成或失败） 以及其返回的值

#### 回调与promise

- callback && callback() 常用写法

- ```javascript
  function f(){
      return new Promise(resolve =>{
          //要执行的操作，调用resolve
      })
  }
  
  f()
  .then(//function1  就是resoleve
  return f()
  )
  .then(//function2 
  return f()
  )
  .then(//function3 
  )
  ```

  

#### 信任问题

- 回调函数不能保证什么时候去调用回调，以及使用什么方式去调用回调；而Promise一旦被确认成功或失败，就不能再被更改。
  另，传统方法无法保证回调只执行一次，并且不会被第三方的某个库进行添油加醋的操作；而Promise调用且仅调用一次resolve()，不会产生回调多次执行的问题。所以Promise很好地解决了第三方工具导致的回调多次执行（控制反转）的问题

#### 错误处理

- then(resolve,reject)
  - resolve 成功时做的事情
  - reject 失败时做的事情
- catch可以对失败进行处理
- finally 收尾工作 一定会处理

#### promise的状态

- pending 进行中
- fulfilled 成功
- rejected 失败
- 状态的改变不可逆，一旦决议就不能再改变

#### Promise.all()

- 把多个promise实例包装成一个新的promise实例  promise.all([p1,p2,p3])
- 空数组，决议为成功

#### Promise.race()

- 只要有一个决议，就立马返回
- 空数组，永远挂起

#### Promise.resolve()

- 传递一个普通的值，决议为成功，并填充这个值
- 传递一个promise实例，直接返回传递进去的promise实例
- 传递一个thenable，具有then方法的对象
  - 包装成promise对象，执行对象里面的then方法
- resolve是异步的

### Class

#### 基本语法

- 类与对象，面向对象，封装

- 类生成一个对象

- ```javascript
  class Car{
      //构造函数
      constructor(wheel,color,length,width){
          //属性
          this.wheel=wheel;
          this.color=color;
          this.length=length;
          this.width=width;
          this.speed=0;
      }
      //方法
      speedup(){
          this.speed+=1;
      }
  }
  //实例化
  const car=new Car(4,"blue",20,40);
  ```

#### 静态方法与静态属性

- 不会被类实例拥有，只有类自身拥有，只能通过类调用
- static 声明方法
- 静态属性声明：Classname.属性名=属性值

#### 类表达式

- const Person=class  name{ }
- name 在外部取不到，只能在类内部取到

#### getter与setter

- 在ES5中

  - 在对象字面量中书写get/set方法

  - ```javascript
    const obj={
        _name:"",
        get name(){
            return this._name;
        },
        set name(val){
            this._name=val;
        }
    }
    ```

  - ```java
    var obj={
        _name;""
    };
    Object.defineProperty(obj,"name",{
        get:function(){
            return this._name;
        },
        set:function(val){
            this._name=val;
        }
    })
    ```

- 在ES6中

  - ```javascript
    class Person{
        constructor(){
             _name:""
        }
        get name(){
            return this._name;
        }
        set name(val){
            this._name=val;
        }
    }
    ```

  - 

#### name属性与new.target

- 返回类的名字

- new.target 只能在class内部访问或者函数内部，访问到的是new关键字后面的这个类

#### ES5模拟类

- 构造函数，当用new调用一个函数时，这个函数就会作为构造函数

- 构造函数原理

  ```javascript
  function constructor(fn,args){
      var _this=Object.create(fn.prototype);
      var res=fn.applt(_this,args);
      return res?res:_this;
  }
  ```

  

#### class继承

- extends
- 写在构造函数里，super(父类的参数) //调用父类构造函数，同时子类的constructor里面也要有这几个参数
- super作为对象的方式调用
  - 非静态方法中访问super   -》父类原型
  - 静态方法中访问super -》父类
- 调用super的时候，父类的this是子类的this

#### 多态

- 同一个接口，在不同情况下做不一样的事情