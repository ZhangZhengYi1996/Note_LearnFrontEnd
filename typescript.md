1. js的超集，有静态类型，js中是动态类型，可以随时改变
2. 安装ts，ts-node



# 基础语法

### 静态类型

1. 具备这个类型的所有属性和方法

### 基础类型

- number
- string
- nu l l, undefined, symbol,boolean,void

### 对象类型

- {}
- number[],string[]
- class
- ()=>number,返回值为number的函数

### type annotation 类型注解

- 定义变量的时候告诉ts变量是什么类型

### type inference 类型推断

- 定义的时候没有直接写明变量类型，ts自动的尝试分析变量
- 如果ts可以分析变量，不需要额外操作
- 如果ts不能分析变量类型，就需要类型注解

### 函数相关类型

- function demo():number {} 返回值为number

- void空，没有返回值

- never类型  这个函数不会执行到最后

- 函数参数解构

  ```typescript
  function add({first,second}:{first:number,second:number}):number{
    return first+second
  }
  ```

### 其他

- Date类型
- let demo:number | string 变量是number或者string

### 数组

- (number|string)[]

- {name:string}[] 数组中的每一项都是{}

- Type alias 类型别名

  ```typescript
  type User={name:string;age:number};
  let objectArr:User[]=[{}]
  ```

### tuple元组

- Demo:[string,string,number] 一共只有三项的固定的数组
- csv文件 可以用元组管理

### interface接口

- interface Person{ name:string;} 定义通用的类型

- Age?:number 表示age可有可无

- readonly 属性只读 不能赋值

- \[propName:string]:any  表示还会有其他任意的属性

- say():string 方法

- class User implements Person 定义一个类应用接口

- interface Teacher extends Person{} 继承

- 定义函数接口  interface Say{

  (Word:string):string

  }.   传入的参数是string 返回值是string

### 类

- 定义与继承

```typescript
class Person{
  name='zzy';
  getName(){
    return this.name;
  }
}
const person =new Person();

class Teacher extends Person{
  getTeacherName(){
    return 'teacher';
  }
  //对父类的方法进行重写
  getName(){
    return 'teacher';
    return super.getName();//使用super调用父类的方法
  }
}
```

- private protected public 访问类型

  ```typescript
  class Person{
    //属性默认public
    //public允许在类的内外被调用
    public name:string;
    say(){
      console.log(this.name);
    }
    //private 允许在类内使用
    //protected 允许在类内以及继承的子类中使用
  }
  const per=new Person();
  per.name='zhang'；
  per.say();
  ```

- Constructor 构造器

  ```typescript
  class Person{
    /*传统写法
    public name:string;
    constructor(name:string){
      //创建实例的时候自动执行
      this.name=name
    }
    */
    
    //简化写法
    constructor(public name:string){ }
  }
  const per=new Person('zzy');
  
  ```

  ```typescript
  class Person{
    constructor(public name:string){}
  }
  class Teacher extends Person{
    constructor(age:number){
      super('zzy');//调用父类的构造函数,需要传参数
    }
  }
  ```

- 静态属性

  ```typescript
  //_name是private的时候 无法直接调用
  get getName(){
    return this._name
  }
  set setName(name:string){
    this._name=name;
  }
  person.getName //不需要括号
  ```

- 单例模式

  ```typescript
  class Demo{
   private static instance:Demo
   private constructor(name:string){}//外部无法调用，不能new实例
   static getInstance(){
     if(!this.instance){
       this.instance=new Demo('zzy');
     }
      return this.instance;
    }//挂在类上，而不是实例上
  }
  
  const demo1=Demo.getInstance();
  ```

- 抽象类

  ```typescript
  abstract class Demo{
    width:number;
    getType(){
      return 'demo';
    }
    abstract getArea():number;
  }//抽象类只能被继承
  
  class Circle extends Demo{
    getArea(){//抽象方法要自己实现
      return 123;
    }
  }
  ```

  

# 爬虫功能开发

- ts中无法直接引用js
- .d.ts 翻译文件
- superagent
- Cheerio

# 语法进阶



# 项目接口



# 高级语法

