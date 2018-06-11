标签分类

1.块标签，能设置宽高，独占一行。eg：div dl(自定义列表) h1（标题标签）

hr(水平分割线 ) p  pre hl ol table 

2.行内标签：不能设置宽高，且不独占一行。宽高由内容撑开。eg：a、span、 b

br(换行) code（引入代码）em i

3.行内块标签：能设置宽高，且不独占一行，eg：img input（输入框）

标签的转换：

1.转化为行内标签：添加属性display:inline；

2.转换为块标签：display：block；

3.转换为行内块标签：display：inline-block；

display： none，用来设置元素的隐藏，并且不占据空间。

a/div标签包图片：会有两像素到4像素的间隙，间隙和font size（字体大小）有关

```html
img{
  	display:block;
	width:100%;
	height:100%;
}
或
给父元素写font-size 0px;
```

**盒子模型：**

1.四个部分：

内容：

内填充:内容到边框的距离padding

​	问题：会撑大盒子

​	解决：在盒子的宽高减去相应的数值，缩小盒子的宽高；

padding四个值代表上 右 下 左

  		三个值上 左右 下

​               两个值 上下 左右

​               一个值 四个方向

边框；

border

border: 10px solid #000;(粗细，样式，颜色)

border-top:10px solid #000;

border-bottom:10px solid #000;

border-left:10px solid #000;

border-right:10px solid #000;

border-top:none;



外间距：盒子与盒子之间的距离。margin

margin-top：10px;

margin-bottom：10px;

margin-left：10px;

简写 margin：0 auto； 使块元素水平居中

盒子模型中的问题：

1.浏览器的一些默认样式 body变迁有8px的外边距

```css
*{
  margin：0；
  padding：0；
}
```

*通用选择器：选中页面中的所有标签

2.margin可以设置负值，padding不可设置负值；

3.行内标签不能设置margintop（没有上下外边距，只有左右外边距）

4.盒子的真实宽高：

宽：width+padding -left+padding-right+border-left+border-right

高：height+padding-top+padding-bottom+border-top+border-bottom

5.当重复设置同一个区域时，会显示较大值，

解决方法；给上面的盒子设置下边距，给左边的盒子设置右边距。

6.

继承属性 font text line color

a标签字体颜色不能继承,需要单独设置

7.a标签设置宽高的情况

float：left;可以视为行内块标，需要改变排布方式才使用

不改变排列方式display: block;

布局要遵循文档流：从左到右，从上到下。

8.子元素添加margintop的bug同时具备五个条件

​	问题描述：给子元素添加margin top，好像作用于父元素身上。

出现问题的五个原因

（1）子元素为父元素的第一个子元素

（2）父元素没有设置内填充

（3）父元素没有边框

（4）子元素没有浮动

（5）父元素没有浮动

​	解决方案：

（1）给父元素一个内填充，用padding-top模拟子元素的margin-top。

（2）给父元素加一个overflow-hidden（超出部分隐藏）。

（3）给父元素添加position :absolute;

(4)给父元素添加float：left;

选择器：

1后代选择器：通过父元素选中子元素，

css：父元素 （空格） 子元素 有类名的情况下优先选择类名，没有类名采用标签名

html：父子关系。

```css
.parent .child
```



优先级直接相加

2群组选择器：共用同样的样式

​	css 选择器与选择器之间用英文状态下的逗号隔开

```css
.a,.b
```



3交叉选择器：同时满足两个条件的标签会被选中

​	类名.标签 a.box

图片的引用

需要经常更新的用img标签

不需要更新的用背景图片

​	背景图片的引入background-image：url先找到路径

​		禁止重复background-repeat：no-repeat；

​		位置background-position：20% 20%;

​			单词：水平 left center right

​				垂直 top center bottom

​			百分比

​			像素：图片精灵(雪碧图)(使用图片精灵不添加background-size),通过坐标调用

​		简写：

​		background：color url no-repeat position ;

​		写背景图片的步骤：

​		先写一个盒子：设置宽高背景色 

​		引入背景图片，设置背景图片大小。background-size 

​		把图形变成圆border-radius：50%

## 浮动：改变排布方式的时候使用

​	float left   float right

浮动的元素会脱离文档流，

浮动的卡顿问题：当某一个元素的高大于其他元素就会发生卡顿，低于则不卡顿。

浮动的bug

​	问题描述：父元素不设置高度，所有的子元素都浮动，浮动的子元素撑不开父元素的高度

​	解决方法：

1能设置高度尽量设置高度

2父元素添加overflow ：hidden

3.在父元素最后加一个子元素，并对子元素添加clear：both



列表标签

<ul>——列表容器

<li>——列表项

都是块标签

样式list-style：none；去掉默认点样式

鼠标移入

选择器 hover

属性 属性值

字体效果标签

粗体 b strong（强调） 搜索引擎strong>b

斜体 i em（强调） 搜索引擎em>i

删除线标签  s 

换行br

下划线标签

​	<div></div> 

​	text- decoration underline；（css中设置）

水平线

```html
<hr width="100" size="10" color="pink" >
水平线 宽度 高度 颜色
标题标签<br>属于块标签（换行）
<h1>一级标题<h1>一共六级，<h3>三级标题<h3>
<h2>二级标题<h2>
段落标签
<p></p>P标签一般不嵌套其他标签，可以嵌套字体标签
<pre> </pre>会按照编辑器预先定义好的格式去展示，
一般使用P标签	
```

4列表标签 块标签

无序列表

```html
<ul type="circle">（空心圆）（disc实心圆）（square方形）
  <li>1</li>
   <li>2</li>
   <li>3</li>
</ul>
```

有默认的填充和边距

有序列表

```html
<ol type="a">(i小写的1 2 3 4 )（I大写的1 2 3 4）
  	<li>1</li>
    <li>2</li>
    <li>3</li>
    <li>4</li>
  </ol>
```

自定义列表

```html
<dl>
  条目<dt>
  具体内容<dd>
```

H5中的语义化标签

```html
<header></header>头部
<footer></footer>（底部）
<nav></nav>导航
<aside></aside>侧导航
<section>页面中独立的内容</section>
<main>主题 内宽</main>
<article>文章的独立内容</article>
<hgroup>文章标题
	<h4></h4>	
</hgroup>
<code>代码</code>
```

透明度

```html
div{
  widt
	heigh
background：rgba(0,0,0,0)(最后的数字代表透明度，取值0~1,数值越大，透明度越低)
}
```

a标签引入图片

```css
display block(不改变排布方式) or float（改变排布方式）
width
height
img width
	height
```

banner图的定位

找到父元素设置添加position：relative;

子元素添加position：absolute;

选择器

伪元素选择器：选中页面中不真实存在的部分

::first-line 选中一行文本

```css
P::first-line{
  color:red;
}
```

选择第一个字母

```css
p::first-letter{选中第一个文本
  color:pink;
}
```

```CSS
div::before{   元素内部前面插入
  conter:"";
  display:block;
  weidh:;
  heidht:;
  backgound
}8
div::after{    元素内部后面插入
  conter:"";
  display：block;
  width:;
  height:;
    
}
```

过渡：

```CSS
:hover
{
  transform:rotate（360deg）;（旋转）
  transition:all 3s       cubic-bezier（） 1s;（必须写前两个属性）
    	属性名称 运动时间      运动方式      延迟
  	{transition-property 属性名称
   	transition-duration运动时间
  	transition-timing-function运动方式
      transition-delay延迟}
  transform：translateX(水平方向平移)   
  transform：translateY (垂直方向平移)
  transform：translate（x y）斜向平移
  transform：scale（X水平 Y垂直 不写则整体放大）（倍数）
  transform：skew(斜切)（度数）
```

i阴影；

```CSS
box-shadow:( X Y 模糊程度 阴影大小) rgba()颜色及不透明度
```

伪类选择器

一、child更注重位置

```css
first-child{}(选中第一个子元素)
last-child{}（选中最后一个子元素）
nth-child(2){}（第二个元素）  *（括号内写2 3 4 代表第几个元素
							2n、even代表偶数元素 2n+1、odd代表奇数元素）
nth-last-child(2)			*(代表选中倒数第二个元素)
```

二、first-of-type选中某种类型的第一个，会忽视其他类型

​	nth-of-type（n）会选中某种类型的第n个，忽视其他类型

属性选择器

```CSS
E[attr="box"](匹配E 元素，且有attr属性, 属性值为box)
	eg:div[class="box"](p匹配div元素的class属性，属性值为box)
E[attr|="box"](匹配E 元素，且有attr属性, 属性值中有连字符，属性值以box开头包括它本身)
	eg:div[class|="box"]会选中
			div calss="box"和div class="box-box1"
E[attr~="box"](匹配E 元素，且有attr属性, 属性值中有空格，属性值包含box，包括它本身)
eg:
div[class~="box"]会选中
	box、 box box1、box1 box
E[attr*="box"](匹配E 元素，且有attr属性, 属性值包含box字母的）
eg:
div[class=*box]会选中
box box1 box1-box...
E[attr^="b"](匹配E 元素，且有attr属性, 以b开头）
E[attr$="x"](匹配E 元素，且有attr属性, 以x结尾）
```
子代选择器（直系父级：）

```CSS
div>p{
  选中直系父级为div的P元素
}
div{
  <a>
  	<p></p>
  </a>
 p不会被选中 
}
```

同级元素

```css
div+p{div后面紧跟着的p标签，兄弟元素仅选中相邻的一个元素}只能写标签名
div~p{所有的紧跟在div后面的p标签 所有的}
```

opacity:0;（透明度0 代表全透明，1代表显示））（占据空间）

display ：none（不占据空间）

伪类选择器

​	根元素hetml标签的选择

```CSS
:root
```

定位：

一、相对定位：（元素发生层叠关系使用用）

​			positio：relative;（父元素）

​			position：absolute;（子元素）（通过top left right bottom进行调整）

​			水平居中left：0;                                      垂直居中top:0;

​					right：0;                                   bottom:0;

​					margin-left: auto;			   margin-top:auto;

​					margin-left: auto;			   margin-bottom:auto;

​	*

​	父元素只需要有定位属性就可以实现定位，

​	如果未对父元素定义属性，那么子元素相对于整个文档进行定位。

二、绝对定位：position：absolute;（通过top left right bottom进行调整）参考元素本身的位置。进行定义。

三、固定定位：相对于窗口定位

position：fixed;

（通过top left right bottom进行调整）

z-index:999（使层级最高）只有使用定位才使用

表单标签

```html
<form action="a.php" method="post"></form>
  action 数据提交位置
  method 数据提交方式
  	get:数据量少  不安全 出现在地址栏
  	post：输入量多 安全 不出现在地址栏
```

控件·输入框

```html
 <form action="a.php" method="post">
	<fieldset>
	<legend>基本信息</legend>
	姓名<input type="text" placeholder="请输入用户名" name="username" ><br><!-- placeholder请输入 -->
	密码<input type="password" placeholder="请输入密码" name="psw" ><br>
	照片<input type="file" name="file"><br><!-- fire上传文件 -->
	请选择你喜欢的音乐<input type="checkbox" name="music[]">爵士<!-- CheckBox多选框 -->
					<input type="checkbox" name="music[]">摇滚
					<input type="checkbox" name="music[]">纯音乐<br>
	请选择你居住的城市<input type="radio" name="city">北京<!-- name相同才可单选 -->
						<input type="radio" name="city">上海
						<input type="radio" name="city">深圳<br>
	请选择你喜欢的网站<select name="" id="" size="3"><!-- size控制显示个数 -->
							<option value="">新浪</option>
							<option value="">雅虎</option>
							<option value="">搜狐</option>
							<option value="">腾讯</option>
							<option value="">百度</option>
						</select><!-- 下拉框 -->
						</fieldset>
	请留言<textarea name="" id="" cols="200" rows="5"></textarea><br><!-- cols水平大小，rows垂直大小 -->
						<!-- 去除拖拽，新建表单css，css中设置resize(是否允许用户进行大小的重新设置):
						none不允许
						both允许
						horizontal水平
						vertical垂直 -->
						<input type="submit"><!-- 提交 -->
						<input type="reset"><!-- 重置 -->
						<input type="button" value="搜索"><!-- 按钮 -->
						</form>
<input type="text" placeholder="" name="" size="" maxlength="" readonly="" disabled="" value="">placeholder="">placeholder输入提示文本name 和数据库交换信息size设置控件宽度maxlength最大输入字符数readonly只读 disabled禁用value获取用户输入内容
```



线性渐变

属性 background-image

linear-gradient-（top red yellow）

第一个参数渐变开始的方向（单词 top left ）

​						角度 0deg=left 90deg=bottom

第二个参数 渐变开始的颜色可以用单词 16进制 rgba写

最后一个参数 渐变结束颜色

不均匀渐变

linear-gradient（颜色和参数要空格）

repeating-linear-gradient-（top,green, red 15%, yellow 20%）					

*第一个元素后加百分比代表在百分之多少之前为纯色，第二个元素之后的百分比代表在百分之多少处出现一条纯色的线条，最后一个元素后加百分比代表百分之多少之后为纯色。

重复渐变

-webkit-repeating-linear-gradient（top red yellow10% green 20%）

最后一个元素的百分比代表结束位置，第一个元素一般不加百分比，

径向渐变

-radial-gradient（50px 50px,color,color）

径向渐变重复

repeating-radial-gradient

倒影（倒影不占据空间，所以设置时需要给给盒子加一个相同大小的外间距）

新建盒子设置宽高插入图片

box-reflect(left 0px none)

第一个属性代表倒影的方向above代表上 below代表下，left代表左，right代表右

第二个属性值代表倒影与原图之间的距离，特别注意，即使倒影与原图没有间隙，也要标注为0px；

第三个属性代表遮罩效果，none代表没有遮罩，

​					URL（引入图片，只显示透明部分）

​					渐变遮罩 -webkit-linear-gradient(top, rgba, rgba)top方向与原图方向一致

rgba(0 ,0,0,0.0)全透明，倒影被遮挡，

rgba(0,0,0,1.0)全黑，倒影可以看得见

rgba（0,0 ,0，0.5）半透明，倒影呈现模糊效果。

用户界面

多列 column-count:n;（n代表列数）

​	column-gap:n em;   列欲裂之间的距离(em 是相对于文字大小的单位，若未设置font-size，则默认em=16px)

​	column-rule:1px solid/dashed color

​	列与列之间加装饰线，（实线solid,虚线为dashed）

物理视口转化外逻辑视口

移动端布局

​	没有鼠标移入效果

视口：可见区域。

​	软件提供的视口一般为980，称之为物理视口

物理视口到逻辑视口的装换：

​	meta：name“viewport” content=“width=device-width”

​	

​	以百分比布局为主，以rem布局为辅。

​	百分比一般为宽度，

​	rem:为具体数值。表示高度，相对根元素的字体大小

​	rem=height/100, 100px=1rem;

​	新建JS文件夹，

​		<script src="js/rem.js">

​	需要修改js的宽度，为设计稿的宽度。

​	box-sizing:border-box;在大盒子内添加边框和填充不用减去相应的宽高。

弹性布局

```css
display: flex;
	justify-content: space-around;
主轴方向flex-direction: row;（水平方向项目排布从左向右）（默认值）
		   flex-direction: row-reverse;（水平方向项目排布从右向左）
		    flex-direction: column;（垂直方向项目排布从上向下）
		   flex-direction:column-reverse;（垂直方向项目排布从下向上）
项目的换行nowrap不换行
	flex-wrap: wrap（从上向下换行）
	flex-wrap: wrap-reverse;（从下向上换行）
项目在主轴方向的对齐方式
    justify-content: flex-start;（主轴起点 左对齐）
    justify-content: flex-end;（主轴终点 右对齐）
    justify-content: center;（主轴中点 居中分布 项目中间无空隙）
    justify-content: space-between;（项目两端对齐（两端没有空隙），剩余空间平均分布）
    justify-content: space-around;（项目两端距离相等 项目中间有空隙）
项目在交叉轴的对齐方式
  		align-items: flex-start(交叉轴起点)
		align-items: flex-end(交叉轴起点)
          align-items: center;(交叉轴中点)
          align-items: baseline;(基于基线对齐，文字底端)
项目在交叉轴方向的对齐方式（基于多轴）
alien-content: flex-start;（交叉轴起点 左对齐）
    alien-content: flex-end;（交叉轴终点 右对齐）
    alien-content: center;（交叉轴中点 居中分布 项目中间无空隙）
    alien-content: space-between;（项目两端对齐（两端没有空隙），剩余空间平均分布）
    alien-content: space-around;（项目两端距离相等 项目中间有空隙）
```

项目的属性

```css
1 1order
.item {
  order: <integer>;(属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。)
}
2flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。
.item {
  flex-grow: <number>; /* default 0 */
}
如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。
3 flex-shrink属性
flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。
.item {
  flex-shrink: <number>; /* default 1 */
}
如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。
负值对该属性无效。
4 flex-basis属性
flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。

.item {
  flex-basis: <length> | auto; /* default auto */
}
它可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间。
4.5 flex属性
flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。

.item {
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}
该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。
建议优先使用这个属性，而不是单独写三个分离的属性，因为浏览器会推算相关值。
4.6 align-self属性
align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。

.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```

## 3D场景的建立

```html
{

perspective: 1000px;(可视为灭点)

}
```

### 观察者视角

```html
perspective-origin: left top;
```

### 使子元素实现3D

```html
transform-style: preserve-3d;
```

### 3D旋转

```html
transform: rotate3d(90deg, 0, 0, angle)(1代表在此条轴旋转)
```



## 动画

### 1定义动画，

```css
@keyframes 动画名称{
  0%{
	background: red;/属性 属性值/
}
20%{
	background: greenyellow;
}
50%{
	background: gold;
}
100%{
	background: #656486;
}
 }
```

### 定义动画的第二种方法

```css
@keyframes 动画名称{

from to

}

```



### 2绑定到相应的选择器上，

```css
animation: bianse 2s;{动画名称 动画时间}

animation-name：动画名称；

animation-direction: 动画时间；

animation-timing-function:ease; 运动方式

animation-delay: 动画延迟，只作用于第一次，第二次动画不显示延迟。

animation-iteration-count:  infinite（无数次）;动画次数，默认为1次。

animation-direction: 反向（alternate）

animation-fill-mode: forwards（停止）最终状态

animation-play-state: paused（静止）running（运动）
```





 ## 响应式页面布局：

一个页面可以适应各个终端

优势：可以减少工作量，很好的用户体验灵活适用不同屏幕的分辨率；

缺点：代码冗余，加载速度慢，

阈值

正常的布局

header{

​	width 100%;

}

大于1024像素

@media screen and （min-width：1024px）

​                设备			阈值 

小于1024像素

@media screen and （max-width ：1024px）（各个值之间要用空格隔开 ， 1024px后不写分号）

padding  0 24px;

文字渐变：

设置文字大小fontsize

设置渐变background-image：-webkit-linear-gradient（left，red，yellow）

给文字设置透明：-webkit-text-fill-color：transparent；

作用于文字：-webkit-background-clip: text;

栅格系统：

快速实现响应式布局

把每一屏幕平均分成12列

预定义类，往元素身上添加；

匹配三种终端 ，四种屏幕大小，<768手机，768~992平板端，992~1200PC小屏，大于1200PC大屏；

input type

<!-- 自动聚焦 -->
<label for="man">（for写IDname）

```html
男：<input type="radio" name="sex" id="man">（要写ID实现自动聚焦功能）
</label>
```
<label for="women">
```html
女：<input type="radio" name="sex" id="women">
</label>
```
<!-- 日期 -->
年月日
<input type="date"><br>
年月
<input type="month"><br>
年周
<input type="week"><br>
时分
<input type="time"><br>
年月日时分
<input type="datetime-local">
范围：
数字：
<input type="number" min="0" max="100" step="5" value="0"><!-- (min范围最小值 max范围最大值 step点击增加值 value初始值) -->
滑块
<input type="range" max="10" min="0" step="2" value="0"><br>
正则
email：
<input type="email">
url
<input type="url"><br>
电话
<input type="tel">
颜色
<input type="color">
进度条
<progress min="0" max="10" value="5"></progress>
范围
<meter min="0" max="10" value="1"></meter>
音频
<audio src="" controls="controls" loop=" loop" autoplay="autoplay"></audio><!-- (src引入文件 controls显示控件 loop循环播放 autoplay自动播放) -->
视频
<video src="" controls="controls" loop=" loop" autoplay="autoplay"></video><br>
画布
<canvas style="width: 300px; height: 300px; background: #bababa; "></canvas>
<link rel="shortcut icon" href="title.png">(title图标的引入)
帧窗口技术：
一个页面可以分为各个窗口去显示，各个页面之间有联系可以相互操作，
<iframe src="" frameborder="1" class=".iframe" name=""></iframe>

锚链接

a链接，即将跳转的地方写mao

<a name="mao"></a>
<a href="#mao">clike me</a>

<table border="1px" cellspacing="0" cellpadding="10px" align="center" width="500px">
​	 border边框 	cellspacing单元格与单元格的间距 cellpadding单元格与内容的距离  align表格整体在水平方向的排布 表格的宽度

	<thead>表头
		<tr><caption>1707信息表</caption>标题
		<th>姓名</th> 行
		<th>性别</th>
		<th>联系方式</th>
		<th>家庭住址</th>
		</tr>
	</thead>
	<tbody>主题
		<tr>
			<td>张三</td>列
			<td>张三</td>
			<td>张三</td>
			<td colspan="">张三</td>跨行合并
			<td>张三</td>	
		</tr>
			<tr align="center">
			<td>张三</td>列
			<td>张三</td>
			<td>张三</td>
			<td colspan="">张三</td>跨行合并
			<td>张三</td>	
		</tr>	<tr>
			<td>张三</td>列
			<td>张三</td>
			<td>张三</td>
			<td colspan="2">张三</td>跨行合并
			
		</tr>
	</tbody>
	<tfoot>表尾
		<tr></tr>
	</tfoot>
</table>

tr:align文本在水平方向的对齐方式

​	valign文本在垂直方向的对齐方式

td colspan 列合并

​	rowspan 行合并

bgcolor单元格背景色设置

css3的新特性。

用css实现水平，垂直居中

span与div的区别

css引入方式
1.外部引入法：外部样式表

```html
link标签
内容与表现分离
```
2.嵌入式：
```html
<style>
.box{
	width: 100px;
	height: 100px;
}
</style>
一般放在head标签中<style></style>标签对
```
3.行内样式
	<div ></div>
写在每一行中，用style属性写
4.导入样式
在一个css中引入另个css @import url('');
优先级：行内样式 >嵌入式=外部（谁写在后面，用谁的样式）
鼠标样式

[div](http://www.divcss5.com/){ cursor:default }默认正常鼠标指针
2）、div{ cursor:hand }和div{ cursor:text } 文本选择效果
3）、div{ cursor:move } 移动选择效果
4）、div{ cursor:pointer } 手指形状 链接选择效果
5）、div{ cursor:url(url图片地址) }设置对象为图片

	a:link{
		color: green;
	}
	a:hover{
		color: red;
	}
	a:active{
		color: yellow;
	}
	a:visited{
		color: skyblue;
	}
</style>
基础选择器：标签 类名 id 后代 通用 群组 交叉
伪类选择器：first-child :hover :focus
:root
真实存在的元素
伪元素选择器::before ::after ::first-line :first-letter
不是真实存在的DOM元素
属性选择器:^ ~ & | * = 
选择器的优先级 style>id>伪类 属性 class >伪元素 标签>通用
文本属性： .text{
```css
width: 200px;
font-size: 50px;
white-space: nowrap;(不换行)
overflow: hidden;（超出部分隐藏）
text-overflow: ellipsis;（以省略号形式显示）
text-transform:  lowercase （小写） uppercase（大写）
text-transform: capitalize;（首字母大写）
letter-spacing: （字间距 可以用像素写，也可以用em写）
p{
	text-indent: 2em;（首行缩进）
}
实体
©	&copy;	©	版权标志
2常用的
 	&nbsp;	 	空格
4 数学类
<	&lt;	<	小于号
>	&gt;	>	大于号
```

行内块标签在垂直方向上的对齐方式 默认基于基线（baseline）对齐
vertical-align: bottom top middle

背景图片引入

	设置宽高、
	background: url('') no-repeat;
	background-size: cover(容器没有空白，图片不能完整显示，宽高中的较小者占满容器);
						contain( 容器有空白 图片可以完整显示，宽高中的较大者占满容器)
logo的引入{

​	<title>Document <link rel="shortcut icon" href=".png"></title>

}

```html
overflow: hidden;（超出部分隐藏）
display: none;（不占据空间 认为元素不存在）
visibility: visible;（隐藏，但元素还存在 可以认为和opacity一样）
```

#### img消除缝隙

`display:block;`	

给父元素设置，`font-size:0;`

设置`float:left`

设置`vertical-align: middle;`