	I.overflow:hidden对float的影响
	通常：因为float元素脱离了文档流，所以包围它的div不占据空间（height和width都
	为默认0的前提下），代码和显示效果如下：
	@code
	.new { background-color : gray; border: solid 1px black; }
	.news img { float : left; }
	.news p { float : right; }
	<div>
		<img src="" alt=""/>
		<p>Some text</p>
	</div>	
		===================================
		|``````||`````````````````````````|
		|______||_________________________|
		[最上面为div，下面是float元素]
	如果想让float元素看起来包含在div中，此时窝们可以修改一下：
	.clear { clear : both; }
	在p元素下面添加：
	<br class="clear" />
	看上去img和p元素又在div中了：
		------------------------------------
		||``````||````````````````````````||
		||______||________________________||
		------------------------------------
	overflow属性定义在包含的内容对于指定的尺寸太大的情况下元素应该怎么样。在默认
	情况下，内容会溢出框外，进入相邻的空间。应用值为hidden或auto的overflow属性有
	一个有用的副作用，这会自动地清理包含的任何浮动的元素。
	
	II.CSS3 border-image属性[border-image参数：图片url,裁剪位置,重复性]
	图片(border-image-source):使用url()调用,如果没有设置为none;
	图片裁剪位置(border-image-slice):(1)(2)(3)
		(1)没有单位话专指像素px,例如:border-image:url(border.gif) 27 repeat;这里27就是像素
		(2)支持百分比,百分比的大小是相对应图片而言.假设图片大小为400px*300px,则20%就是裁剪
		图片的60px,80px,60px,80px的四边大小;
		(3)裁剪特性:按照上右下左的顺序进行裁剪,30% 35% 40% 30%意思为在距图像上面30%地方裁剪
		一下,在距图像右侧35%地方裁剪一下,在距图像下部40%的地方裁剪一下,在距图片左侧30%的地方
		裁剪一下,把一个图像分成9份.
	3.重复性(border-image-repeat):三个参数供选择，默认stretch(拉伸),还有round(平铺)和
		repeat(重复).参数使用时为0~2个,1个时表示水平和垂直均使用该参数,2个时第一个参数表示
		水平方向,第二个参数表示垂直方向.
		例如:border-image:url(border.png) 30% 40% round repeat;表示水平方向平铺,垂直方向重复.
		
	/*border-image绘制原理简述*/

	1、调用边框图片
		border-image的url属性,通过相对或绝对路径链接图片.
	2、边框图片的剪裁
		border-image的数值参数剪裁边框图片,形成九宫格.
	3、剪裁图片填充边框
		边框图片被切割成9部分,以一一对应的关系放到div边框的九宫格中,然后再压缩(或拉伸)至边框
		(border-width或border-image-width)的宽度大小.
	4、执行重复属性
		被填充至边框九宫格四个角落的的边框图片是不执行重复属性的.上下的九宫格执行水平方向的重复
		属性(拉伸或平铺),左右的格子执行垂直方向的重复属性,而中间的那个格子则水平重复和垂直方
		向的重复都要执行.
	5、完成绘制，实现效果
	@code
	.border_image{
	    width:400px;
	    height:100px; 
	    -moz-border-image:url(image/border.gif) 27/20px repeat; 
	    -webkit-border-image:url(image/border.gif) 27/20px repeat; 
	}
	注：27/20px是窝希望边框的宽度为20px,所以在CSS中设置的.
	
	III:CSS3 Gradient
	1.Mozilla 下
	-moz-linear-gradient( [<point> || <angle>,]? <stop>, <stop> [, <stop>]* )
	参数:其共有三个参数,第一个参数表示线性渐变的方向,top 是从上到下、left 是从左到右,如果定义成 left
	top,那就是从左上角到右下角.第二个和第三个参数分别是起点颜色和终点颜色.你还可以在它们之间插入更多的
	参数,表示多种颜色的渐变.
	2.Webkit 下
	-webkit-linear-gradient( [<point> || <angle>,]? <stop>, <stop> [, <stop>]* )//最新发布书写语法
	-webkit-gradient(<type>, <point> [, <radius>]?, <point> [, <radius>]? [, <stop>]*) //老式语法书写规则
	参数：-webkit-gradient 是 webkit引擎对渐变的实现参数,一共有五个.第一个参数表示渐变类型（type）,
	可以是linear（线性渐变）或者radial（径向渐变）.第二个参数和第三个参数,都是一对值,分别表示渐变起点
	和终点.这对值可以用坐标形式表示,也可以用关键值表示,比如 left top（左上角）和left bottom（左下角）.
	第四个和第五个参数,分别是两个color-stop函数.color-stop函数接受两个参数,第一个表示渐变的位置,0为起点,
	0.5为中点,1为结束点;第二个表示该点的颜色.
	3. Opera 下
	-o-linear-gradient([<point> || <angle>,]? <stop>, <stop> [, <stop>]); /* Opera 11.10+ */
	参数：-o-linear-gradient 有三个参数.第一个参数表示线性渐变的方向,top 是从上到下、left 是从左到右,
	如果定义成 left top,那就是从左上角到右下角.第二个和第三个参数分别是起点颜色和终点颜色.你还可以在
	它们之间插入更多的参数,表示多种颜色的渐变.（注:Opera 支持的版本有限,本例测试都是在 Opera11.1 版
	本下,后面不在提示）
	4. Trident (IE) 下
	filter: progid:DXImageTransform.Microsoft.gradient(GradientType=0, startColorstr=#1471da,
	endColorstr=#1C85FB);/*IE<9>*/
	-ms-filter: "progid:DXImageTransform.Microsoft.gradient (GradientType=0, startColorstr=#1471da,
	endColorstr=#1C85FB)";/*IE8+*/
	IE依靠滤镜实现渐变.startColorstr表示起点的颜色,endColorstr 表示终点颜色.GradientType 表示渐变类型,
	0 为缺省值,表示垂直渐变,1 表示水平渐变.
	
	IV.CSS围住浮动元素的三种方法
	第一种:父元素应用overflow:hidden,以强制它包围浮动元素
	第二种:让父元素浮动起来
	第三种:给父元素的最后添加一个非浮动的子元素,然后清除该子元素.
	(1)*div元素
	(2)*使用clearfix规则
	
	@code
	<!DOCTYPE html>
	<html>
	<head>
	   <meta charset="utf-8">
	   <title>Examples</title>
	   <style>
	
	   section {border:1px solid blue; margin:0 0 10px 0;}
	   p {margin 0;}
	   footer {border:1px solid red;}
	   img {float:left;}
	   </style>
	</head>
	<body>
	   <section> 
	       <img src="test.gif" />
	       <p>It's fun to float.</p>
	   </section> 
	   <footer> Here is the footer element that runs across the bottom of the page.</footer> 
	</body>
	</html>
	第一种:
		section {border:1px solid blue; margin:0 0 10px 0; overflow:hidden;}
	第二种:
		section {border:1px solid blue; margin:0 0 10px 0; float:left; width:100%;}
		footer {border:1px solid red; clear:left;}
	注意:浮动非图片元素时,必须给它设定宽度,否则后果难以预料
	第三种:
	(1)	<body>
		    <section class="clearfix"> 
		        <img src="test.gif" />
		        <p>It's fun to float.</p>
		        <div class="clear_me"></div>
		    </section> 
		    <footer> Here is the footer element that runs across the bottom of the page.</footer> 
		</body>
		<style>
			section {border:1px solid blue; margin:0 0 10px 0;}
			p {margin 0;}
			footer {border:1px solid red;}
			img {float:left;}
			.clear_me {clear:left;}
		</style>

	(2)	<section class="clearfix"> 
			<img src="test.jpg"> 
			<p>It's fun to float.</p> 
		</section>
		.clearfix:after { 
			content:"."; 
			display:block; 
			height:0; 
			visibility:hidden; 
			clear:both; 
		}
	浮动是实现多栏布局（在更多浏览器支持CSS3的Multi-column Layout Module之前）唯一最可靠的方式
	
	V.为什么行内元素(例如<a>)设置float之后才能用width调整宽度?
	只有块元素才会有物理属性,在css世界里边,有三种形态的东西

	1. 块元素特性:有物理属性,width,height写值起作用,而且要占据一行
	2. 内联元素特性:没有物理属性.但是margin,padding值有用,不占据一行,后边可以有兄弟元素
	3. 即是块又是内联,根据兄弟元素决定
	
	为什么是float之后才会有物理属性,这就是块与内联元素相互转化的问题.
	块元素->内联元素: display:inline;
	内联元素->块元素: display:block;
	
	[***]float就是隐性的把内联元素转化为块元素,这是对内部的特性就是有物理特性,但是他不占据一行.
	对外是内联元素的属性.他有个坏处就是会影响兄弟元素.相当于display:inline-block;
	那为什么不直接display:inline-block;因为这个XX在ie6下有几个px的bug
