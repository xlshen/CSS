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

<a name="dynamic"></a>动态伪类选择器  
<a name="target"></a>目标伪类选择器  
<a name="language"></a>语言伪类选择器  
<a name="ui"></a>UI伪类选择器  
<a name="construct"></a>结构伪类选择器  
<a name="deny"></a>否定伪类选择器  
