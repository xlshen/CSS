	1.overflow:hidden对float的影响
	通常：因为float元素脱离了文档流，所以包围它的div不占据空间（height和width都
	为默认0的前提下），代码和显示效果如下：
	
	@Code
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
	
	2.CSS3 border-image属性[border-image参数：图片url,裁剪位置,重复性]
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
