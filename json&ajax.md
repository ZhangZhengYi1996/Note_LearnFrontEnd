# Ajax

### 什么是Ajax

- 异步的js和xml，是几种技术的结合体
- 无需重新加载整个网页的情况，能够更新部分网页

### Ajax的优点

- 通过异步模式，提升用户体验
- 优化浏览器与服务器之间的传输，减少不必要的数据往返，减少带宽占用
- Ajax引擎在客户端运行，承担了一部分本来由服务器承担的工作，减少了大用户下的服务器负载

### 缺点

- 不支持浏览器back按钮
- 安全问题：暴露了与服务器交互的细节
- 对搜索引擎的支持比较弱

### XMLHttpRequest对象

- 支持异步请求的技术，Ajax的核心
- 向服务器提出请求并处理响应，不阻塞用户
- 在页面加载以后进行页面的局部更新

### 如何使用Ajax

- 创建XMLHttpRequest对象（异步调用对象）
- 创建一个新的http请求，并指定该http请求的方法，url
  - open(method,url,async)
  - 功能：创建http请求，规定请求类型，url及是否异步请求
  - method：请求类型，GET 或POST
  - url：文件在服务器上的位置
  - async：异步true或同步false
- 设置响应http请求状态变化的函数
  - 请求发往服务器——服务器根据请求生成相应——传回给xhr对象
  - responseText:从服务器进程返回数据的字符串形式
  - responseXML:从服务器进程返回的dom兼容的文档数据对象
  - status:从服务器返回的数字代码如404
  - status Text:伴随状态码的字符串信息
- 发送http请求
  - send 把请求发送到服务器
  - string仅用于post请求
  - 使用setRequestHeader添加HTTP头
    - setRequestHeader("Content-type","application/x-www-form-urlencoded")
- 获取异步调用返回的数据
- 使用js和dom实现局部刷新

### jquery的ajax方法

- $.ajax()
- $.get()
- $.post()
- $.getJson()

# json

- JavaScript对象表示法，是一种数据格式
- 可以表示三种类型的值
  - 简单值: 字符串，数值，布尔值，null
  - 不支持undefined
  - 对象
  - 数组
- json对象
  - json.parse() 转为对象
  - json.stringify() 转为字符串

# 跨域

- 同源策略：域名 协议 端口均相同
- 跨域：从一个域名的网页去请求另一个域名的资源
  - 只要协议 域名 端口任何一个不同就是跨域

### 如何解决跨域

- 跨域资源共享（cors）
- ==jsonp（常用）==
  - json with padding 填充式json
  - 回调函数：响应到来时应在页面中调用的函数
  - 数据：传入回调函数中的json数据
- 修改document.domain
- 使用window.name