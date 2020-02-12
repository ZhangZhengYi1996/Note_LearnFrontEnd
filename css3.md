# css3选择器

### 基本选择器

- 子元素   （直接后代）
  - father>children 

- ==相邻==兄弟元素
  - element + sibling
- 通用兄弟（下面的所有兄弟）
  - element~sibling
- 群组
  - 元素1，2，3

### 属性选择器

- element[attribute="value"]
- element[attribute~="value"] 包含value
- element[attribute^="value"] 开头
- element[attribute$="value"]   结尾
- element[attribute*="value"]   包含字符串
- element[attribute|="value"]   为value或者value==-==开头

### 伪类选择器

- 动态伪类
  - :link, :visited, :hover, :active, :focus
- ui元素状态伪类
  - :enabled 可输入
  - :disabled
  - :checked 只用于单选按钮和复选框，目前主流的浏览器都能兼容

- 结构类
  - :first-child
  - element: last-child  最后一个元素是element
  - :nth-child(N)
  - :nth-child(==n==) n从零开始
    - 2n 偶数，2n+1 奇数/ odd，even 
    - 3n+1...
    - 不支持*
  - :nth-last-child(N) 倒数 从最后一个开始 
  - :nth-of-type(N) 
  - :nth-last-of-type(N) 
  - :first-of-type
  - :last-of-type
  - element: only-child 唯一元素且是element
  - :only-of-type
  - :empty 没有子元素及内容的每一个元素 空元素
- 否定选择器 不需要选中的
  - ：not（子元素/子选择器）

### css权重

- 行内100>id 10>类、属性、伪类 10 > 元素和伪元素1>* 0
- 与元素挨得近 更高
- div head top right 一长串没有class高

### 伪元素

用于向某些选择器设置特殊效果

元素：：伪元素 

- **：：first-line** ==第一行文本== 用于==块级元素==

- ：：first-letter

-  ：：before ==内容==前面插入新内容 配合==content==

  - 是第一个子元素
  - 是行级元素

- ：：after 内容后面

  - 是最后一个子元素
  - 是行内元素
  - 配合content 多用于清除浮动

  ```::after{displat:block; content:"";clear:both }```

  - ::selection 设置选中文本后的背景色和前景色

***

# 边框与圆角

### 圆角

- border-radius
  - 50% 变成椭圆
  - 顺时针，从左上角开始


### 盒阴影

- box-shadow：h v blur spread color inset

### 边界图片

- border-image-: source slice width outset repeat 
  - source :url
  - slice: 图像边界向内偏移 fill
  - width 边界宽度  
  - outset： 外部绘制边框的量 边框往外、扩张

***

# 背景与渐变

### 背景

#### 背景图像区域

- background-clip 指定绘制区域

#### 背景图像定位

- background- origin  指定background-position相对位置

#### 背景图片大小

- background-size
  - cover：等比缩放填满
  - contain：等比缩放至某一边紧贴容器边缘

#### 多重背景图像

- background-image ： url1， url2

#### 背景属性整合

- color position size repeat origin clip attachment url

### 线性渐变linear gradients

#### 线性

- background: linear-gradient(方向 ，颜色1， 颜色2)

  - 默认 上至下

- 左到右

  -webkit 开始方向

  -moz 结束

  -0 结束

  to 结束

- 斜对角

  -webkit 开始水平  开始竖直

  -moz，-o 结束水平 结束竖直

  to

#### 角度 

-  ==使用角度== background: linear-gradient(角度 ，颜色1， 颜色2)
  - 0deg 下到上
  - 90deg 左到右
  - 默认方法 顺时针

#### 重复渐变

- background: repeating-linear-gradient

### 径向渐变

#### radial gradient

- 从内到外圆形渐变
- radial-gradient（中心，形状尺寸（不加逗号）,....）
- 形状：circle，ellipse
- 尺寸：最近边 最远边 最近角 最远角

#### 重复渐变

- repeating-radial-gradient

#### ie 渐变

- ie 6-8
- filter:progid:DXImageTransform.Microsoft.gradient



# 文本与字体

### 文本

- 兼容性不好

#### 文本阴影

- text-shadow：h v blur color
- 文本轮廓text-outline：粗细 blur color  基本都不兼容

#### 换行

- word-break 规定自动换行的处理方法
  - normal break-all keep-all
- word-wrap 长单词或url换行到下一行

#### css3 新文本属性

<span id="text" name="text"> text</span>

- text-align-last 对齐文本的最后一行
  - 要配合text-align：justify

- text-overflow：clip，ellipsis
  - 要配合overflow：hidden

### 字体

#### @font-face

- @font-face{

  font-family   自定义字体名称

  src                  存放路径

  font-weight   

  font-style

  }

- 字体格式format
  - .ttf
  - .otf
  - .woff
  - .eot
  - .svg
- 获取特殊字体 

# 转换

### transform属性 2D转换 

- rotate（角度） 指定角度旋转 正顺负逆
- translate 移动 translateX translateY 以及xy一起
- scale 缩放 X Y 同时 比例 不需要单位
- skew 斜切扭曲

### 3D转换

- rotate X Y Z 在轴上旋转
  - rotate3d（x,y,z,deg) 1,1,1,deg   0或非0, 表示程度
- translateZ 平移
  - translate3d（x，y，z）
- scaleZ z轴缩放
  - scale3d（x,y,z）

### transform与坐标系统

- transform-origin 更改转换基准点
  - 左上角 left top

### css3矩阵

- transform:matrix(a,b,c,d,tx偏移量,ty偏移量)  3*3

- matrix（sx,0,0,sy,0,0)=scale(sx,sy)

- matrix(cos,sin,-sin,cos,0,0)=rotate(deg)

- matrix(1,tandegy,tandegx,1,0,0)=skew(x,y)

- matrix(1,0,0,1,x,y)=tranlate(x,y)

- 可以实现镜像效果

  - ```
    matrix((1-k*k) / (1+k*k), 2k / (1 + k*k), 2k / (1 + k*k), (k*k - 1) / (1+k*k), 0, 0)
    ```

- 3d 4*4 matrix3d
  
  - transform: matrix3d(sx, 0, 0, 0, 0, sy, 0, 0, 0, 0, sz, 0, 0, 0, 0, 1) =scale

### 扩展属性

- transform-style：flat|preserve-3d
- perspective：number|none
  - perspective-origin：x y 默认值50% 50%
- backface-visibility : visible | hidden

# 过渡 transition 

- transition-property 指定过渡的属性名称
  - none all 属性名（color,opacity...)
- transition-duration:time  过渡的持续时间
- transition-timing-function
- - linear
  - ease 平滑
  - ease-in 慢到快
  - ease-out 快到慢
  - ease-in-out
  - step-start , step-end
  - steps
- transition-delay
- ==简写顺序== property duration timing-function delay

# 动画

### animation

- animation-name 

  - @keyframes name{ 

    from{}

    to{}

    }

- animation-duration

- animation-time-function

- animation-delay

- animation-iteration-count 循环次数

- animation-direction

- animation-fill-mode 完成或未播放时 呈现什么状态

- animation-play-state 是否运行 paused，running

- ==顺序== name duration time-function delay 循环次数  方向 fill-mode play=state

### keyframes

- 动画变化的关键位置

### 动画性能优化

- will-change 增强页面渲染性能  提前让浏览器准备优化设置
- GPU 图形处理器 

- auto ，srcoll-position，contents，明确的属性

# 多列布局

### multi - column

- columns: 每一列宽度 列数
  
- 优先列数
  
- column-width:length/auto

- column-count:number/auto

- column-gap: length/normal  列之间的间隙

- column-rule：列之间的边框 

  - 宽度 样式 颜色

  - -width：length thin medium thick
  - -style：solid dotted ...
  - -color

- column-span 横跨所有列 none/all

- column-fill : auto/balance 高度是否统一

  - 都不兼容

-  column-break 

  - -before 检索对象之前是否断行 auto always avoid 
  - -after
  - -inside ：auto/avoid

# 用户界面

- appearance 主流浏览器都不兼容 要加内核前缀
- text-overflow： clip|ellipsis    见新文本属性 
- white-space:nowrap;设置的是容器中的文字强制不换行，一行显示完全，overflow:hidden;设置的是容器内容超出部分隐藏，只有文字在一行中的显示超出容器时，容器设置超出部分隐藏，text-overflow才能起作用将隐藏的部分以何种形式展示。
- outline 设置或检索对象外的线条轮廓 
  - 在border外面 不占据布局控件 不影响元素尺寸
  - outline：宽度 样式 颜色
  - outline-offset 轮廓偏移
- nav-index：auto /值 设置或检索对象的导航顺序
- cursor 
- zoom 设置或检索缩放比例
- box-sizing ：content-box/ border-box
- resize 只能拉大 不能缩小 
  - 需要设置元素的overflow 属性，值可以是 auto、hidden 或 scroll
- ime-model 输入法
- user-select 是否允许选中文本
- pointer-events