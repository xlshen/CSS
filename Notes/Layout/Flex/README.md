### CSS Flexbox
> Flex是Flexible Box缩写，用来为盒装模型提供灵活性,考虑到PC浏览器兼容性问题，现主要应用与移动端Web布局

采用`Flex`布局的元素我们称为`flex container`,它里面所有的子元素称为`flex item`
容器默认存在两根轴：水平主轴(`main axis`)和垂直交叉轴(`cross axis`)。主轴开始位置为`main start`，结束位置为`main end`；交叉轴开始位置为`cross start`，结束位置为`cross end`。
单个`item`占据的主轴空间为`main size`，垂直空间为`cross size`。
#### Flexbox属性
> 1. flex-direction  
2. flex-wrap  
3. flex-flow  
4. justify-content  
5. align-items  
6. align-content  

##### flex-direction
> 决定主轴的子元素排列方向

```html
.box{
  display: flex;
  flex-direction: row(default)【→】 | row-reverse【←】 | column【↓】 | column-reverve【↑】;
}
```
##### flex-wrap
> 决定子元素在水平方向排列不下如何换行

```html
.box{
  display: flex;
  flex-wrap: nowrap(default) | wrap【换到下一行排列】| wrap-reverse【还行到上一行排列】
  //如果父元素flex-wrap:wrap，子元素设置了宽度，则子元素的宽度失效
}
```
##### flex-flow
> flex-flow: flex-direction flex-wrap的缩写

##### justify-content
> 决定子元素在主轴上的对齐方式

```html
.box{
  display: flex;
  justify-content: flex-start(default)【左对齐】 | flex-end【右对齐】 | center【居中】| space-between【两端对齐】 | space-around【子元素左右间隔相等，两个子元素之间间隔是最外子元素到边框的距离的2倍】;
}
```
##### align-items
> 决定子元素在交叉轴对其方式

```html
.box{
  display: flex;
  align-items: flex-start【顶部对齐】 | flex-end【底部对齐】 | center【垂直居中对齐】 | baseline【第一行文字基线对其】 | stretch(default)【拉伸对齐】;
}
```
##### flex-content
> 多根轴线的对齐方式，如果只有一根则该属性不起作用【本人测试在Chrome下只有一行也起作用...】

```html
.box{
  display: flex;
  align-content: flex-start(default)【多行顶部对齐】| flex-end【多行底部对齐】 | center【多行居中对齐】 | space-between【垂直两端对齐】 | space-around【每行子元素上下间隔相等，子元素之间间隔是最上距离边框距离2倍】 | strech【兼容性不好，各浏览器表现不一】 
}
```
#### 子元素属性
> 1. order  
2. flex-grow  
3. flex-shrink  
4. flex-basis  
5. flex  
6. align-self  

##### order属性
> 定义子元素排列顺序，数值越小排列越靠前，默认为0。

```html
.item{
  order: <integer>;
}
```
##### flex-grow属性
> 决定子元素放大比例，默认为0，即如果存在剩余空间，也不放大。

```html
.item{
  flex-grow: <number>;/* default 0 */
}
```
此属性决定父元素如果比子元素宽度大，则对`剩余空间`进行按比例分割填充
##### flex-shrink属性
> 决定子元素缩小比例，默认为1，即如果空间不足，该子元素将缩小

```html
.item{
  flex-shrink: <number>;/* default 1*/
}
```
此属性决定父元素空间不足时，子元素缩小比列控制
##### flex-basis
> 决定了分配多余空间之前，子元素占据的主轴空间。浏览器根据这个属性，计算主轴是否有多余的空间

```html
.item{
  flex-basis: <length> | auto; /* default auto*/
}
```
可以设置固定的值，则子元素占据固定的空间
##### flex属性
> flex属性是flex-grow flex-shrink flex-basis的缩写，默认值为 0 1 auto。后两个可选

```html
.item{
  flex: none | [<'flex-grow'> <'flex-shrink'>? || <'flex-basis'>]
}
flex-grow 是扩展比率
flex-shrink 是收缩比率
flex-basis 伸缩基准值
第一种情况：父元素宽度 < 子元素总宽度
子元素伸缩值计算方式：
① 加权值： item = (flex-shrink) * flex-basis, 加权值 = item1 + item2 + ... + itemN;
② 压缩后宽度： (子元素flex-basis值 * (flex-shrink)/加权值) * 溢出值
注：此时计算时，子元素的margin和padding单独从总的宽度中减不参与计算！
```
##### align-self属性
> 允许单个子元素与其他子元素不一样的对齐方式，可覆盖`align-items`属性。

```html
.item{
  align-self: auto(default)【表示继承父元素的align-items属性】 | flex-start | flex-end | center | baseline | stretch;
}
```
