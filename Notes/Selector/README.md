### CSS选择器
***
#### 1. 基本选择器
```javascript
* //通配符选择器，匹配所有HTML元素
E //元素选择器，匹配指定HTML元素
#id //ID选择器，匹配ID属性为“id”的元素
.class //类选择器，匹配class属性为“class”的属性
selectorA,selectorB //群组选择器，匹配元素集合
```
#### 2. 层次选择器
```javascript
E F //后代选择器，匹配元素F，且F是元素E的后代
E > F //子选择器，匹配元素F，且F是元素E的直接子元素，非直接子元素不起作用
E + F //相邻兄弟选择器，匹配元素F，且F是元素E后面紧邻的兄弟元素，兄弟元素子元素不匹配
E ~ F //通用兄弟选择器，匹配元素F，且F是元素E后面所有兄弟元素，兄弟元素子元素不匹配【CSS3】
```
#### 3. 伪类选择器
>[3.1 动态伪类选择器](#dynamic)  
>[3.2 目标伪类选择器](#target)  
>[3.3 语言伪类选择器](#language)  
>[3.4 UI状态伪类选择器](#ui)  
>[3.5 结构伪类选择器](#construct)  
>[3.6 否定伪类选择器](#deny) 

<a name="dynamic"></a> 
##### 3.1 动态伪类选择器
```javascript
E:link //匹配元素E，且该元素定义了超链接并未访问过
E:visited //匹配元素E，且该元素定义了超链接并已经访问过
E:active //匹配元素E，且该元素被激活
E:hover //匹配元素E，且鼠标停留在该元素上
E:focus //匹配元素E，且该元素获得焦点
```
链接伪元素设置顺序：LoVe||HAte原则：link-visited-hover-active
<a name="target"></a>
##### 3.2 目标伪类选择器
```javascript
E:target //匹配元素E，且该元素被相关URL指向【CSS3】
//IE9+
```
<a name="language"></a>
##### 3.3 语言伪类选择器
>语言伪类选择器是根据元素的语言编码匹配元素，这种语言信息必须包含在文档中或与文档关联，不能从CSS指定。为文档指定语言有两种方式：

1 . 如果HTML5，直接设置文档语言：
```javascript
<html lang="en-US">
```
2 . 手工在文档中指定lang属性，并设置对应的语言值：
```javascript
<body lang="fr">
```
```javascript
E:lang(language) //匹配元素E，且该元素指定了lang属性且其值为language
```
<a name="ui"></a>
##### UI伪类选择器
>UI元素主要用于form表单元素，一般包括：启用、禁用、选中、未选中、获得焦点、失去焦点、锁定等

```javascript
E:checked //匹配元素E，且该元素被选中【单选按钮或复选按钮】【CSS3】
E:enabled //匹配元素E，所有启用的表单元素【CSS3】
E:diabled //匹配元素E，所有禁用的表单元素【CSS3】
//IE9+
```
<a name="construct"></a>
##### 结构伪类选择器
>根据DOM结构树层次结构匹配特定的元素

```javascript
E:first-child //匹配第一个子元素E，与E:nth-child(1)等同【CSS3】
E:last-child //匹配最后一个子元素E，与E:nth-last-child(1)等同【CSS3】
E:root //匹配元素E所在文档的根元素，在HTML文档中始终为html元素【CSS3】
E F:nth-child(n) //匹配父元素是E，第n个子元素F，其中n可以是整数、关键字（odd）、公式（-n+1），而且n起始值为1【CSS3】
E F:nth-last-child(n) //匹配顺序与上面正好相反，其中nth-last-child(1)始终匹配最后一个元素【CSS3】
E:nth-of-type(n) //匹配父元素指定类型的第n个子元素E【CSS3】
E:nth-last-of-type(n) //匹配顺序与上面正好相反【CSS3】
E:first-of-type //匹配父元素指定的第一个该类型的子元素E，与nth-of-type(1)等同【CSS3】
E:last-of-type //匹配父元素指定的最后一个该类型的子元素E，与nth-last-of-type(1)等同【CSS3】
E:only-child //匹配父元素只包含的唯一一个子元素E【CSS3】
E:only-of-type //匹配父元素指定类型的唯一一个子元素E【CSS3】
E:empty //匹配没有子元素的元素E【CSS3】
//实例
<div>
    <ul> //ul:only-of-child
        <li>one<li> //li:first-child[nth-child(2n+1)]
        <li>two<li> //li:nth-child(2)
        <li>three<li> //li:last-child[nth-child(2n+1)]
    </ul>
    <p>paragraph</p> 
    <div>ddd</div> //div div:first-of-type
    <p>message</p> //p:nth-of-type(2)
    <b>bbb</b>
</div>
//IE9+
```
<a name="deny"></a>
##### 否定伪类选择器
```javascript
E:not(F) //匹配所有除元素F以外所有的元素E【CSS3】
//IE9+
```
这是个非常有用的选择器，用来定位不匹配该选择器的元素
