# 栅格化布局

### 规则

- div class="container"  调试内外边距和对齐方式
- 默认12列   还需要行 div class="row"
- 具体内容放在列元素之内，列元素是row的直接子元素
  - class="col-..."
  - col-md-number(表示占多少列)
  - col-md-offset-num(偏移)
- 可以嵌套
  - row嵌套在col中
- col-md-push-num 元素向右移动
- col-md-pull-num 向左浮动
- 栅格参数  响应式
  - xs 超小屏幕 768px
  - sm 平板 >768
  - md 中等 >992
  - lg 超大 1200
- clearfix 清除浮动

### 一些class

- pull-left pull-right
- 小三角 caret

# 模块分类及排版布局

### 模块分类

- 基础 颜色 尺寸 状态 特殊元素 并列 嵌套子元素 动画

### 排版布局

- 标题 class= h1~h6  36px 30px 24px ...
- 页面主题 class=lead
- title=“。。。”
- 地址  address标签<address> </address>
- ul li 
  - 清除圆点 class=“list-unstyled”
- 内联列表 class=“list-inline”
- 水平自定义列表 dl dt dd class=“dl-horizontal”

### 表格及表单样式

#### 表格

- class="table"
- table-striped 隔行变色
- table-bordered 边框
- table -hover
- 行与列
  - class="active" 背景色 当前查看
  - success 提示颜色 成功
  - info 信息
  - warning 警告
  - danger 报错

#### 表单

- form-group label和input一组

- form-control

- 按钮 btn btn-default

- 内联表单

  - form-inline

  - sr-only

- 水平排列

  - form-horizontal

- checkbox disabled等class

- 静态控件

  - form-control-static

- 校验

  - has-success
  - has-warning
  - has-error

- 图标反馈 

  - glyphicon glyphicon-ok
  - -warning-sign
  - -remove

### 按钮及其他

#### 按钮

- class="btn" 
- btn-default
- btn-primary
- btn-success
- btn-info
- btn-warning
- btn-danger
- btn-link
- btn-lg sm xs
- btn-block 父元素宽度100%
- active 激活  disabled禁用
- 可以用于超链接

#### 图像

- img-rounded
- img-circle 
- img-thumbnail

#### 文本

- text-primary
- text-muted
- -success warning danger

#### 关闭图标

#### 下三角

- caret

#### 常用

- pull-right 右浮动
  - pull-left和pull-right不能用于导航条组件中，排列导航条中的组件时可以使用这些工具类：.navbar-left 或 .navbar-right 
- center-block
- clearfix 清除浮动

# 常用组件

- 组件：能直接使用的图标 效果等

### 图标

- 基本使用：内联元素 基本类 图标类
- 基类：glyphicon
  - class=“glyphicon glyphicon-user”
  - input-group-addon

### 下拉菜单

- 调用js jquery
- class="dropdown"包裹 
  - dropdown-toggle datatoggle="dropdown"
- dropdown-menu
- divider 下拉菜单边框
- 按钮组 btn-group
- 按钮工具栏 btn-toolbar
  - btn-group   -lg/sm/xs 

### 按钮式下拉菜单

-  btn-group
  - button dropdown-toggle data-toggle
  - dropdown-menu
- 输入框 input-group   lg/xs/sm
  - input-group-addon

### 导航

- nav nav-tabs
- nav-pills
- nav-justified  

### 导航条

- navbar navbar-default 背景色 边框色
- navbar-header
- navbar-brand
- navbar-nav

### 分页 标签 徽章 巨幕

### 缩略图 警告条 列表组 面板

### 插件





