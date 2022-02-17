
### 1.什么是像素

~~~ text
像素就是屏幕中的那些发光发亮能显示特定颜色的小点 
~~~



###  2.什么是物理像素 

~~~ text
物理像素又称设备像素,指的是设备上的像素点 

一个设备的物理像素是固定的,一经生产不可改变
~~~



### 3.什么是逻辑像素

~~~ text
逻辑像素又称为css像素,就是编程中给某个元素设置的px 

===>浏览器在显示网页的时候,把我们布局使用的css像素转为设备像素然后渲染 

那么1个逻辑像素永远===1个css像素吗? 不一定这个由设备像素比决定  
~~~



### 4. 设备像素比(DPR) 

~~~ text
设备像素比的英文是`device pixel ratio` 所以设备像素比又叫做DPR 

DPR = 物理像素 / 逻辑像素 

设备像素如何获取：`window.devicePixelRatio `
~~~



### 5.移动端视口分类

~~~ text
1. 布局视口：用于存放我们页面的一个视口；早期移动端技术没有发展的时候为了让PC端的页面显示在移动端所以存在一个布局视口；布局视口的宽度用`document.documentElement.clientWidth `来获取 

   

2. 视觉视口：眼睛能够看到的部分是视觉视口；视觉视口的面积就是手机设备的面积 

   

3. 理想视口：理想视口（又叫做完美视口）是一个概念指的是当布局视口的大小正好等于视觉视 口的宽度,这样写的页面才完美无瑕,这样的一种视口称为理想视口 
~~~





### 6.如何实现完美视口

```html
<meta name="viewport" content="width=device-width,initial-scale=1.0,minimumscale=1.0,maximum-scale=1.0,user-scalable=no">
```

### 7.盒模型组成部分

~~~ css
margin border padding content
~~~



### 8.标准盒模型和怪异盒模型的区别

```css
1.标准盒模型下元素的width只是元素内容的宽不包含padding border;如果为元素添加了padding和
  border那么向外扩充该元素
  
2.怪异盒模型下元素的width是padding,border和content这三部分组成,如果为元素添加padding
  和border那么向内压缩元素的内容部分
```



### 9.盒模型转换

```css
1. box-sizing:content-box;表示的是设置的盒子width值从元素的内容部分算起 也就是标准盒模型 

2. box-sizing:border-box;表示的是社会组的盒子的width值从元素的边框部分算起 也就是怪异盒模 型  

```

### 10.屏幕分类

```css
1.超小屏: 屏幕物理像素小于768px的   以前小屏幕手机如老年机屏

2.小屏： 屏幕的物理像素大于768px小于992px的   主流的手机屏幕

3.中屏： 屏幕的物理像素大于992px小于1200px的  平板电脑

4.大屏:  屏幕的物理像素大于1200px的  PC屏幕
```

### 11.布局单位

~~~css
1.px

2.%

3.rem:以根元素html的font-size为参考

4.em：以自身或者父元素的font-size为参考

5.vw:以屏幕的宽度为参考

6.vh：以屏幕的高度为参考
~~~

### 12. 移动端常见的四种布局方式及特点 

```css
1.流式布局特点：一侧固定,一侧百分比；
	缺点：1.当屏幕变大或者缩小的时候使得元素拉伸或者压缩从而导致变形。
		 2.百分比存在精确度问题,不能百分百还原页面（如33.333333%）
2.响应式布局特点：同一个页面结构,根据不同的屏幕尺寸加载不同的css样式,从而使页面实现自适应
	缺点：同一个元素,在不同尺寸的屏幕下加载多个css样式,代码过于冗余

3.rem布局特点：相对于html的fontsize倍数取值
	缺点：手机横屏不能使用（因为横屏字体会相当大）

4.flex布局的特点：采用关键字取值
	缺点:float布局就会失效,依赖display属性,如果想要实现元素的显示隐藏那关display属性已被占用

```

### 13.响应式布局语法

~~~ css
@media screen and (min-width){}
~~~

### 14.动态设置html字体的方法

~~~ css
1.css中设置

html{
	font-size:calc(100vw * 100 / 设计图的宽)
}
~~~

~~~ css
2.js动态设置

document.documentElement.style.fontSize = 
document.documentElement.clientWidth * 100 / 设计图的宽度 + 'px'

~~~

~~~ css
3.flexible.js插件：该插件的原理是把屏幕的宽度分为10份之后的结果赋值给html的fontSize
~~~

### 15.如何把元素设置为弹性容器

~~~ css
为元素添加 display:flex属性
~~~

### 16.弹性容器上的6个属性

~~~ css
1.设置主轴的方向
flex-direction:

2.设置项目在容器中是否换行
flex-wrap:

3.复合写法
flex-flow:;是flex-direction和flex-wrap的复合写法

4.置项目在主轴上的对齐方式
justify-content:flex-start||flex-end|center||space-between||spacearound||space-evenly设

5.设置单行项目在交叉轴上的对齐方式
align-items:flex-start|center|flex-end|stretch|baseline

6.设置多行项目在交叉轴上的对齐方式
align-content:flex-start||center||flex-end||strech||space-between||spacearound||space-evenly

~~~

### 17.项目上的6个属性

~~~ css
1.order:;设置项目排列顺序；排列规则：值越大越向后排,值越小越向前排,默认值是0

2.flex-grow:;设置是否瓜分主轴的剩余空间,默认值是0 不瓜分

3.flex-shrink:;设置项目是否被压缩,默认值是1代表被压缩

4.flex-basis:;设置项目在瓜分主轴上的剩余空间之前,占用主轴上的空间,默认是auto也就是内容
多宽项目占主轴多少空间,和width的作用一样,但是权重比width的高

5.flex:;是flex-grow flex-shrink和flex-basis的复合写法

6.align-self：；单独设置某个项目在交叉轴上的对齐方式

~~~

### 18.弹性盒考点

~~~css
1.使用弹性盒布局实现一个元素水平垂直居中,写出代码

    <div.box>
        <div></div>
    </div>

    .box{
        width:1000px;
        height:500px;
        display:flex;


        justify-content:center;
        align-items:center;
    }

2.使用flex布局实现上中下的固比固结构

~~~

### 19.css新增的选择器

~~~ css
1.属性选择器
	p[class]
    p[class="active"]
    p[class^='a']
    p[class$='e']
    p[class*=c]
    p[class~=abc]

2.结构伪类选择器
    1.元素:nth-child(n){}
    2.元素:last-child{} 选择的是父元素中的最后一个儿子
    3.元素:first-child{} 选择的是父元素中的第一个儿子
    4.元素:nth-child(2n) even
    5.元素:nth-child(2n+1) odd
    6.元素:nth-child(3n)

3.同类型选择器
    1.元素:nth-of-type(n){}
    2.元素:first-of-type{} 选择的父元素中指定类型的的第一个元素
    3.元素:last-of-type{} 选择的是父元素中指定类型的最后一个元素
    4.状态伪类选择器

4.元素:focus
    input:focus{}
    该选择器选中的是获取焦点的input框

5.元素:disabled
	button:disabled{}
	该选择器选中的是被禁用的button按钮

6.元素：checked
	input:checked{}
	该选择器选中的是被选中的复选框

7.元素::selection/*注意：该选择器的冒号为双冒号*/
	p::selection{}
	该选择器是选中的是p标签中被选中的文本内容

8.伪元素选择器
	1.元素::before{}/*注意这里是双冒号单冒号都可以*/
	该选择器是在该元素的前面添加一个伪元素

	2.元素::after{}/*注意这里是双冒号单冒号都可以*/
	该选择是在该元素的尾部添加一个伪元素,该选择器一般用于清除浮动

	/*注意伪元素选择器创建的元素,只能用来显示,不能用来选中*/

    /*为什么叫做伪元素：看起来和普通元素一样可以设置内容和样式,但是不是真正的dom元素,也
    就是说不能使用js来获取这个伪元素,该元素的内容也不能被选中,只能用来显示*/
~~~

### 20.css3新增的颜色取值

~~~ css 
1.color:rgba() 

2.color:transparent

~~~

### 21.浏览器私有前缀

~~~ css
1.常见浏览器的私有前缀
    Chrome -webkit- 谷歌
    fixfox -moz- 火狐
    ie -ms- IE浏览器
    Opera -o- 欧朋浏览器

2.浏览器私有前缀的作用
	让浏览器更好的识别css3新增的属性
~~~

### 22.css3新增的文字属性

~~~ css
1.文字描边/*注意的是：该属性必须添加私有前缀*/
	-webkit-text-stroke:2px blue; 值为两个参数第一个代表线宽,第二个代表描边颜色

2.文字阴影
	1.text-shadow:水平偏移量 垂直偏移量 阴影模糊程度 阴影颜色,水平偏移1,垂直偏移1,模糊程度

	2.阴影颜色：text-shadow:x y blur color;  
	
3.单行文本溢出省略号显示
    p{
        /*文本超出元素不换行*/
        white-space:nowrap;
        /*超出部分溢出隐藏*/
        overflow:hidden;
        /*以省略号的形式隐藏超出部分*/
        text-overflow:ellipsis;
    }

4.多行文本溢出省略号显示
    div{
        /*这种设置为弹性盒的方式是以前的写法*/
        
        /*注意：属性名和属性值该带私有前缀的必须带私有前缀*/
        display:-webkit-box;//设为弹性盒
        
        /*orient是方向的意思 vertical垂直 horizontal水平*/
        -webkit-box-orient:vertical;//主轴方向为纵向;
        
        /*clamp夹紧,夹子,仅仅显示几行*/
        -webkit-line-clamp:3;//显示几行,超出部分省略号显示
        
        /*超出部分隐藏*/
        overflow:hidden;//超出3行的部分省隐藏
    }
~~~

### 23.css新增的元素属性

~~~ css
1.圆角
    border-radius:5px;/*四个角都是5px圆角*/
    border-radius:1px(左上) 2px（右上） 3px(右下) 4px(左下)
    border-radius:20px 50px;左上右下对角线为20px 右上左下对角线是50px
    border-radius:20px 50px 30px; 左上20px 右上左下对角是50px 右下是30px
    分开写:先写上下 再写左右
    border-top-left:1px;
    border-top-right:2px;
    border-bottom-left:4px;
    border-bottom-right:3px;

2.盒子阴影
    对比文字阴影：text-shadow:2px(水平偏移量) 3px(垂直偏移量) 3px(模糊程度) red(阴影
    颜色)
    box-shadow:2px(水平偏移量) 2px(垂直偏移量) 3px(模糊程度) 3px(模糊大小) red(阴影
    颜色) 默认值是外阴影|inset(内外阴影)
    /*注意：外阴影是默认值,如果想是外阴影那么最后一个值不写即可,如果想是内阴影那么最后一个值
    设置为inset即可*/

3.背景图尺寸（该属性可以写在复合属性中,贴边的时候贴的是父元素的border的最外边）
    background-size:100px(宽) 50px(高)
    background-size:100px;(宽为100px高度自适应)
    background-size:100% 100% 宽度盖度都是父元素的宽高
    background-size:cover(等比例放大,贴俩边,在贴俩边的过程中如果有一个边超出了父元素
    的边框没关系 ,只要最小的那个也贴住父元素的变就停止)
    background-size:contain(等比例放大,有一个边贴到父元素的边框就停止)

4.背景裁剪(该属性不可以写到复合属性中):控制背景的绘制区域,对于背景图的裁剪要求背景图片覆盖
    background-clip:border-box(从边框的外边缘向内开始绘制背景颜色)
    background-clip:padding-box(从内边距的外缘开始向内绘制背景颜色)
    background-clip:content-box(从内容部分开始向内绘制背景颜色)
    /*注意对于背景图片来说border-box和padding-box是一样的的效果*/

5.背景色渐变
    1.线性渐变:(默认值是从上向下渐变,只有两者有交集才会有渐变)
    /*默认值是从上向下渐变,100px代表的是100px以内是红色,从200px开始显示绿色,那么在
    100-200中间是红绿渐变的位置,也可以用百分数来表示*/
    background-image:linear-gradient(red 100px,green 200px)
    /*从左向右渐变,渐变颜色均匀分布*/
    backrgound-image:linear-gradient(to right,red,yellow,blue)
    /*从右下 到左上渐变,颜色均匀分布 (先写上下 再写左右)*/
    background-image:linear-gradient(to bottom left,red,yellow,blue)
    /*从指定的角度开始渐变(0度代表的是从下向上渐变,90deg代表的是从左向右渐变,也就是顺时
    针)*/
    background-image:linear-gradient(0deg,red,yellow)

2.径向渐变
    background-image:radial-gradient(circle|ellipse(渐变图形是圆形或者椭圆,默认
    值是ellipse椭圆),red,yellow)

6.背景属性复合：该属性可以设置多个背景色和背景图,使用逗号隔开即可
    1. background:color,image repeate position/size
    /*如果是多张背景图片的话,背景颜色color需要单独拿出来写 */
    background-color:yellow;

    2. background:image repeate position/size,image1 repeate position/size
~~~

### 24.css3变形

~~~css
为元素添加transform属性实现变形,变形的种类有下述4种

    1./*平移*/
    transform:translate(100px(水平位移的像素,正值是向右位移),100px（垂直位移的像素,正值是向下位移）)
    transform:translate(100px)/*当只有一个值的时候,默认代表的是水平位移*/
    transform:translateX(100px);/*表明某个方向上的位移*/
    transform:translateY(100px)；
    transform:translateZ(100px);/*z轴是垂直于屏幕指向自己的一个轴线,在3D情况下才能看出效果*/

2./*旋转*/：每次只能绕一个轴转不能缩写
    transform:rotate(30deg);/*默认是绕z轴旋转,2D情况下值是正数绕顺时针旋转*/
    transform:rotateX(30deg);/*绕指定的轴线进行旋转*/
    transform:rotateY(30deg)
    transform:rotateZ(30deg)

3./*缩放*/
    transform:scale(2);/*只写一个值的是代表横向纵向均放大2被*/
    transform:scale(1.5,2)/*代表的是水平方向上放大1.5倍,垂直方向上放大2倍*/
    transform:scaleX(1.5)/*代表某一个方向上的缩放*/
    transform:scaleY(0.5);

4./*变形,度数是正值,顺时针倾斜*/
    transform:skew(30deg,60deg)/*第一个参数代表的是水平方向上的倾斜,第二个参数代表的是垂
    直方向上的倾斜*/
    transform:skew(30deg)/*当只写一个参数的时候,代表第二个参数的度数是0deg*/
~~~

### 25.变形原点

~~~ css
1.如果默认不写就是按照元素的中心点进行变形
（transform-origin:center center）
/*这里没有要求说必须先写上下,再写左右,先写那个都可以*/

2.tranform-origin:top left;/*按照元素的左上角进行c3变形*/

3.transform-origin:bottom left;/*按照元素的左下角进行c3变形*/

4.transform-origin:top right;

5.transform-origin:bottom left;

6.transform-origin:center center;

~~~

### 26.3D属性

~~~ css
想要实现3D变形需要为父元素设置透视 perspective(透视的意思)

/*该属性用来设置近大远小的感觉*/
-webkit-perspective:none|length;(none是没有透视没有3D效果,length值是如：800或
800px,值越小近大远小的效果越明显)

/*设置透视的原点,该属性不写的时候,默认值是50% 50%,一般不用设置,使用默认值即可*/
perspective-origin:50%(平视) 50%（俯视）

/*变形的形式 preserve是保持保留的意思*/
transform-style:preserve-3d;/*保持3D变形*/

/*注意：这几个属性设置给父元素,那么其子元素才会有3D变换的效果*/
~~~

### 27.css3新增的过渡动画

~~~ css
为元素添加transition属性实现元素的过渡

/*1.设置过渡属性:*/
	transition-property:width|height|...

/*2.设置过渡时长 单位是秒或者毫秒*/
	transition-duration:1s;

/*3.设置过渡的运动曲线/速度*/
	transition-timing-function:linear|ease|ease-in|ease-out|ease-in-out|cubic|bezier

/*4.过渡动画延迟多久开始过渡 单位是秒或者毫秒*/
	transition-delay:2s

/*注意这些属性添加在元素上,这些属性的过渡需要条件来触发,如鼠标滑过的时候触发,把width属性值设置为更大等*/

/*5.复合写法*/
	transition:过渡属性 过渡时长 过渡速度 过渡延迟;

~~~

### 28.关键帧动画

~~~css
/*1.关键帧动画的定义*/
@keyframes 动画名称{
    0%{

    }

    100%{

    }
}
/*2.关键帧动画的调用*/
	animation:;
/* animation属性来配置动画的属性值*/

    1.动画名
		animation-name:;

    /*为什么设置动画名,因为关键帧动画的动画属性都是放在动画名中进行设置的,
      所以一个元素如果有动画效果必须设置动画名*/

    2.动画完成需要的时间,单位是秒或者毫秒
		animation-duration:2s;

    3.设置动画的运动速度|运动曲线
        animation-timint-function:
        linear|ease|ease-in|ease-out|ease-in-out|cubic-bezier


    4.设置动画延迟多久开始播放,单位是秒或者毫秒
		animation-delay:1s;

    5.设置动画重复次数
		animation-iteration-count:3|infinite;

    6.animation-direction:
        normal(默认值代表是从0%-100%)|
        alternate(0% - 100% - 0%类似一个循环)
        /*这里说的顺时针指的是按照动画设置的方向运动,逆时针指的是和动画设置的方向相反的运动方向*/
        alternate：奇数次顺时针播放动画 偶数次逆时针播放动画
        alternate-reverse:奇数次逆时针播放动画,偶数次顺时针播放动画
        reverse:每次都是逆时针播放动画

    7.animation-fill-mode:none|forwards|backwards|both；
        none代表的是没有填充,默认值,动画结束后保持自身的效果
        forwards:代表的是动画结束后元素保持最后一帧动画的效果
        backwards:代表的是动画开始时元素保持第一帧动画的效果
        both：代表的是元素在动画开始前保持的是第一帧的效果,动画结束时保持的是最后一帧的效果
        backwards（如果该属性不写,默认值是回到初始的第一帧的状态0%的状态）动画结束回到第一帧的状态
        forwards 动画结束回到动画的最后一帧(100%的状态)的状态

    8.关键帧动画的播放状态
    	animation-play-state:running(继续执行,默认值是播放)|paused(停止执行);
~~~

### 29.关键帧动画和过渡动画的区别

~~~ css
1.动画执行的条件不同
	过渡动画需要触发才能执行,关键帧动画不需要鼠标滑过等触发条件；

2.动画定义的方式不同
    过渡动画使用transtion属性来实现；关键帧动画使用animation属性和@keyframes关键字来实
    现
~~~

### 30.H5新增的标签

~~~ css
1.结构类标签
    1.头部标签
    	<header></header>

    2.导航标签
    	<nav></nav>

    3.侧边栏标签:如左侧导航
    	<aside></aside>

    4.文章标签 如论坛CSDN,博客,等大部分文字的网站
    	<article></article>

    5.内容部分标签:主体区域部分
    	<main></main>

    6.段落或楼层标签如京东的楼层效果,一个楼层就是一个section来包
    	<section></section>

    7.底部当行标签
    	<footer></footer>
   
	新增了许多语义化更强的标签,为什么要新增这些标签或者这些标签的优点
        1.语义行更强,方便阅读和协同开发
        2.便于搜索引擎搜索
        3.提高浏览器的识别速度

2.功能类标签
    1.标题组标签-->
    	<hgroup>
             知道是主标题和副标题是一组的即可,所以放入标题组中
            <h1>主标题</h1>
            <h2>副标题</h2>
        </hgroup>
    2.可输入的数据列表标签

        该标签搭配input标签一起使用,list的值和datalist中的id属性中的值保持一直
        <input type="text" list="city">
        <datalist id="city">
            注意点option的内容可以不写但是 value值必须写
            <option value="北京"></option>
            <option value="南京"></option>
            <option value="东京"></option>
            <option value="郑州"></option>
            <option value="徐州"></option>
            <option value="苏州"></option>
            <option value="杭州"></option>
        </datalist>

    3.地址标签: 门户网站尤其是某公司的官网,地址信息不可或缺,写在address中更便于搜索
        <address>
            <span>作者：张三</span>
            <span>年龄：18</span>
            <span>地址：保定</span>
        </address>

    4.高亮-->
    	<mark></mark>

    3.多媒体标签
        <audio></audio>音频
        <video></video>视频

    4.画布标签
		<canvas><canvas>
~~~

### 31.H5新增的input属性

~~~ css
1.placeholder属性 表单的不占位提示文本
	<input type="text" placeholder="请输入姓名">

2.表单禁用属性
	<input disabled>

3.表单只读属性
	<input readonly>

~~~

### 32.H5新增的input的type类型

~~~  css
之前学过的type类型 text radio checkbox submit button password

    1.数字
    <input type="number" min="0" max="10" step="2">

    2.颜色:value值是16进制的颜色值
    <input type="color">

    3.进度条|滑块:如果value代表滑块在进度条的什么部位,默认不写value是在进度条的一半处
    <input type="range" min='1' max=100 value='1'>

    4.电话
    <input type="tel">

    5.url地址
    <input type="url">

    6.邮箱
    <input type="email">

    7.搜索：获取焦点的时候,该输入框右侧有个X号可以清空输入框的内容
    <input type="search">

    8.日期
        1.年月日
        <input type="date">

        2.年月
        <input type="month">

        3.时分
        <input type="time">

        4.所选的年月日属于该年里的第几周
        <input type="week">

        5.年月日时分秒
        <input type="datetime-local">

    9.文件
    	<input type="file">

~~~

### 33.文件上传

~~~ css
1.单文件上传步骤
    1.设置input的type类型为file 并绑定change事件
    2.获取上传的文件列表结合中的上传的文件 var file= this.files[0]
    3.为上传的文件创建文件读取对象 var fr = new FileReader()
    4.如果上传的是图片读取为路径 fr.readAsDataURL(file)；如果是文件读取文件内容
    fr.readAsText(file);读取的结果保存在fr.result上
    5.等待上传完毕 创建节点 并设置内容 fr.onload = function(){}

2.多图片上传步骤
	inp.onchange = function(){
        
	1.获取上传的文件的列表
		var files = this.files;
        
	2.遍历这个列表集合 为上传的每个文件创建读取文件的对象,并读取每个文件
        for(var i = 0 ; i < files.length ; i++){
        var fr = new FileReader()
            
	3.把每个上传的文件读作url格式
		fr.readAsDataURL(files[i])
            
	4.监听读取加载完毕事件
		fr.onload = function(){
            
	5.创建节点对象 并设置图片的src 插入到body中
            
        var img = document.creareElement('img')
            img.src = this.result;
            box.appedChild(img)
            }
        }
        
1.单文件上传步骤
    1.设置input的type类型为file 并绑定change事件
        
    2.获取上传的文件列表结合中的上传的文件 var file= this.files[0]
        
    3.为上传的文件创建文件读取对象 var fr = new FileReader()
        
    4.如果上传的是图片读取为路径 fr.readAsDataURL(file)；如果是文件读取文件内容
    fr.readAsText(file);读取的结果保存在fr.result上
        
    5.等待上传完毕 创建节点 并设置内容 fr.onload = function(){}
        
2.多图片上传步骤
    inp.onchange = function(){
        
    1.获取上传的文件的列表
    	var files = this.files;
        
    2.遍历这个列表集合 为上传的每个文件创建读取文件的对象,并读取每个文件
        for(var i = 0 ; i < files.length ; i++){
        var fr = new FileReader()
            
    3.把每个上传的文件读作url格式
    	fr.readAsDataURL(files[i])
            
    4.监听读取加载完毕事件
    	fr.onload = function(){
            
    5.创建节点对象 并设置图片的src 插入到body中
            var img = document.creareElement('img')
            img.src = this.result;
            box.appedChild(img)
        }
      }

~~~

### 34.音频标签

~~~ css
1.audio标签上的属性(下面这些属性是在<audio></audio>标签上添加的)

    1.src 音频的路径
    2.controls 音频控件
    3.autoplay 自动播放,但是谷歌已把该功能舍去
    4.muted 静音
    5.preload 预加载,文件加载时候是否提前加载音频文件
	6.loop 音频循环播放

	<audio src="音频的url路径" controls ></audio>

2.音频对象的属性（下面这些属性是获取到音频节点对象后获取或设置的）
    1.音频.duration 获取|设置音频的时长
    2.音频.volume 获取|设置音频的音量
    3.音量.currentTime 获取|设置当前的播放到的时间/位置
    4.音频.paused 获取|设置音频是否暂停,值如果设置为true代表是暂停,值如果是
    false代表不是暂停,只有是否暂停的属性,没有是否播放的属性
    5.音频.playbackRate 获取|设置播放速度,正常播放速度是1倍速,返回值是1
	
3.音频对象的方法
    1.音频.play()
    2.音频.pause()

4.音频的事件
    1.ended 监听音频是否播放完
    2.pause 监听音频是否暂停
    3.play 监听音频是否播放
    4.timeupdate 监听音频播放位置是否改变
    5.volumechange 监听声音是否改变

5.各个浏览器能够识别的音频格式不同,为了让浏览器更好的兼容我们的音频使用source标签(不考)
    <audio>
        <source src="不同格式的音频">
        <source src="不同格式的音频">
        <source src="不同格式的音频">
        <source src="不同格式的音频">
        ...
    </audio>
~~~

### 35.视频标签

~~~ css
1.video标签上的属性

    1.src 视频的路径
    2.controls 视频控件
    3.muted 静音
    4.autoplay 自动播放(谷歌浏览器把该功能舍弃)
    5.preload 页面加载的时候预加载视频
    6.loop 循环播放
    7.poster 视频播放前的封面（如抖音发短视频的时候的封面）
    8.width 设置视频标签的宽度
    9.height 设置视频标签的高度

    <video poster="海报图的url地址" src="视频的url路径" width="300" controls></video>

2.视频节点对象上的属性
    1.视频.duration 设置|获取 视频的长度
    2.视频.puased 设置|获取 视频是否暂停
    3.视频.currentTime 设置|获取 视频当前播放到的位置
    4.视频.playbackRate 设置|获取 视频播放倍速
    5.视频.volume 设置|获取 视频的音量

3.视频的方法
    视频.play()
    视频.pause()

4.视频的事件
    1.ended 监听视频是否播放结束,但是该事件不能设置loop循环,因为循环播放永不结束
    2.pause 监听视频是否暂停
    3.play 监听视频是否播放
    4.timeupdate 监听视频播放位置是否发生改变
    5.volumechange 监听视频音量是否改变

5.各个浏览器能够识别的视频的格式不同,为了让更多浏览器兼容我们的视频格式使用source标签
    <video>
        <source src="视频格式1">
        <source src="视频格式2">
        <source src="视频格式3">
        ...
    </video>	
~~~

### 36.touch（触摸）事件

~~~ css
1.移动端触摸事件的分类 (推荐使用dom2级绑定  不建议使用dom0级绑定)

    1.触摸开始: touchstart   只要触摸元素该事件就执行
    2.触摸移动: touchmove    在元素上移动即可触发
    3.触摸结束: touchend     手指移开元素该事件触发
    4.触摸中断: touchcancel  被别的程序打断的时候触发  如：来电话


2.面试题:为什么移动端使用click事件会存在300ms延迟
    
    因为需要在这300ms内等待是否进行第二次单击,如果在300ms进行了第二单击,
    如果在300ms内进行第二次单击那么这两个单击组成一个双击事件


3.触摸事件的事件对象 

	在事件监听器中使用形参 e/ev/event 代表的是触摸事件的事件对象

4.事件对象上的触摸点的分类: 返回值都是类数组 是个集合

    1.event.touches 		获取屏幕上的所有的触摸点
    2.event.targetTouches 	目标元素上的所有触摸点
    3.event.changedTouches 	触摸点状态改变后的所有触摸点
        
5.触摸点中的信息
     e.touches[0].pageX 触摸点到页面的水平距离
     e.touches[0].pageY 触摸点到页面的垂直距离

     e.touches[0].clientX 触摸点到视口(手机设备的)的水平距离*******
     e.touches[0].clientY 触摸点到视口(手机设备的)的垂直距离*******

     e.touches[0].screenX 触摸点到电脑屏幕的水平距离
     e.touches[0].screenY 触摸点到电脑屏幕的垂直距离
~~~

### 37.本地存储

~~~ js
1.浏览器的本地存储：window.localStorage  window.sessionStorage(widow可省)

    1.长期存储
        localStorage  存储的大小 5M  存储周期:永久性存储 除非手动删除

        //增
        localStorage.setItem(属性名key,属性值value)

        //删除
        localStorage.removeItem(属性名)
        localStorage.clear()

        //查 取 用
        localStorage.getItem(属性名)

        localStorage.key(属性名的索引)

        storage事件:用来监听本地存储的内容是否发生改变，
        只要浏览器本地存储中的内容发生改变该事件就会触发   
        (不能在修改的页面内进行进绑定)

        storage事件对象 
        window.addEventListener('storage',function(e){

            e就是事件对象 

            e.key ===>本地存储中那个属性名中的值发生变化了

            e.newValue ===> 修改后的新值

            e.oldValue ===>修改之前的旧值

            e.url  ===> 在哪个页面对该属性进行了修改 url就是该页面的路径

        })


    2.会话存储
    	sessionStorage 存储的大小 5M 存储周期:浏览器关闭 会话存储中的信息全部被删除

            


2.服务端存储 cookie :必须在服务器环境下才能进行存取  document.cookie 存储的大小是 4k

     /*
        属性值 username=张三&userpass=123 是url ?号传参的格式一样  
        userInfo属性名也就是key
        username=张三&userpass=123 属性值 也就是value
    */ 

        // 增 存储
        document.cookie = 'userInfo=username=张三&userpass=123'

        // 使用 查看  取出来的结果'userInfo=username=张三&userpass=123' 自己进行解析
        console.log(document.cookie)

        // 修改
        document.cookie = 'userInfo=username=李四&userpass=456'

        // 删除 通过设置过期时间删除  cookie识别不了毫秒数

        //页面加载获取当前登录时间
        var nowTime = new Date().getTime();
        var nextTime = nowTime + 3000;

        document.cookie = 'userInfo=username=李四&userpass=456;expires='
        +newDate(nextTime).toUTCString();
~~~

### 38.canvas画布

~~~ js
画布的基本使用
1.html中创建canvas标签(画纸)

2.填空题：获取绘制的上下文对象
	var ctx = document.querySelector('canvas').getContext('2d')
​        
3.设置画笔的样式
	1.设置画笔的颜色
		ctx.strokeStyle = 'red';
​       ctx.fillStyle = 'pink';

​   2.画笔的粗细
​       ctx.lineWidth = 5;

4.绘制
​    
​   1.矩形
​       ctx.strokeRect(x,y,width,height) 描边或者线框矩形
​       ctx.fillRect(x,y,width,height)   填充矩形
​       考点：在canvas内每1s绘制一个 大小随机 颜色随机 位置随机的矩形

​    2.圆形
​       ctx.arc(x,y,r,0,Math.PI*2,false)
​       ctx.stroke()
​       ctx.fill()
​       考点：在canvas内每1s绘制一个 大小随机 颜色随机 位置随机的圆

​    3.画线
		ctx.moveTo(x,y)
		ctx.lineTo(x1,y1)
​       ctx.stroke()
​       考点:填空题  自动闭合路径  
​       ctx.closePath()

​       考点: 填空的 在绘制第二个图形的时候 第一个图形会被覆盖重新绘制一次为什么？
​            (两个图形共用同一个路径) 怎么解决(使用ctx.beginPath()重新开辟新的路径)

​	4.绘制文字
		1.设置文字颜色
			ctx.strokeStyle = 'red'
​           ctx.fillStyle = 'yellow'

​       2.设置文字font属性
​           ctx.font = 'style weight size family'

​       3.文字的对齐方式
​           水平
​           ctx.textAlign = 'left/center/right'

​           垂直
​           ctx.textBaseline = 'bottom/middle/top'

​		4.绘制
​            ctx.strokeText('文字内容',x,y)
​            ctx.fillText('文字内容',x,y)

​	5.绘制渐变
​       1.线性渐变
​            1.创建线性渐变  (两个点决定了渐变的方向)
​            	var linear =  ctx.createLinearGradient(startX,startY,endX,endY)

​            2.在该线性渐变上添加渐变颜色
​                 linear.addColorStop(0,"red")
​                 linear.addColorStop(0.5,"yellow")
​                 linear.addColorStop(1,"bule")

​            3.应用到描边或者是填充样式上
​                 ctx.fillStyle = linear

​             4.绘制图形          
​                 ctx.fillRect(0,0,600,600)
​                 ctx.strokeRect(0,0,600,600)

​         2.径向渐变
​             1.创建径向渐变
​                 var radial = ctx.createRadialGradient(x,y,r1,x,y,r2)
​                        
​             2.在该渐变方向上添加渐变颜色
​                 radial.addColorStop(0,"red")
​                 radial.addColorStop(0.5,"yellow")
​                 radial.addColorStop(1,"bule")

​              3.应用到描边或者是填充样式上
​                 ctx.fillStyle = radial

​              4.绘制
​				  ctx.fillRect(0,0,600,600)
​        		  ctx.fillRect(0,0,600,600)

	6.绘制图片(了解)
		js创建img节点对象
​       img.src = ''
​       img.onload = function(){
​       	ctx.drawImage()
​       }

	7.把绘制的图形保存为图片并回显到浏览器的方法
​       1.获取到画布 canvas节点对象
​       2.把画布转为base64格式的图片路径 
​       3.创建img标签 img.src = 把画布转为base64格式的图片路径 
​       4.当img加载完毕之后 把img插入到body中
​       /*
​       	考点：当把图形转为image/jpeg格式的时候如果没有填充色 
​       	默认会添加一个黑色的填充色 解决办法：
​                   
​       	使用绘制矩形的api绘制一个具有填充色的矩形
​       */

	8.画笔的平移 旋转  缩放 
		ctx.translate(x,y)****绘制坐标轴
​       ctx.rotate()
​       ctx.scale()

	9.多图形组合
​            
		1.后画覆盖先画
			ctx.globalCompositeOperation = 'source-over'//默认值

​       2.后画清空先画(用在橡皮擦) (清空的形状 根据自己定义)
​           ctx.globalCompositeOperation = 'destination-out'

	10.清空绘制的区域
​            
		清空矩形区域内的绘制内容(以矩形的形式来清空绘制的内容)
			ctx.clearRect(x,y,width,height)
~~~



