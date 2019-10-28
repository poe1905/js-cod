## jQeury 介绍

### jQuery的概念

* jQuery 是一个快速的 简洁的javaScript 的库,其设计的宗旨是"write less , Do More", 即倡导写更少的代码,做更多的事情.
* j就是javaScript : Query 是查询:   意思是查询js   吧js中的DOM的操作做了封装,我们可以快速使用查询到的元素,使用其中的功能.
* jQuery封装了javaScript 里常用的功能代码,优化了DOM操作,事件处理,动画设计和Ajax交互
* 学习jQuery就是学习调用这些函数(方法).

### jQuery 的优点

* 轻量级
* 跨浏览器兼容
* 链式编程,隐式迭代
* 对事件,样式,动画支持,大大简化了DOM操作
* 支持插件拓展开发,有着丰富的第三方的插件    
* 免费,开源



### $ 是jQuery 的一个别名



```js
例如：
	$('div').hide()  ===》 jQuery('div').hied()
```

* $ 是jQuery 中的顶级对象.

#### jQuery对象和DOM对象之间的转化

* DOM对象

```js
1.通过原生js获取到的对象就是DOM对象
例如: varmydiv = document.quertSelector("DIV"); mydiv 就是 一个DOM对象
```

* 转化为jQuery对象

```js
因为jQuery 是通过$符号来获取对象,
    所以把需要转化的对象放到$(DOM对象) 返回值就是转化后的jQuery对象

```



* jQuery对象

```js
1.通过jQuery的方式获取的对象就是jQuery对象
例如: var mydiv = $("div") ; mydiv 就是一个jQuery对象
```

* 转化为DOM对象
  * 因为获取到的jQuery对象都是以数组的形式存在的, 包括获取到一个元素还是多个元素,
  * 故,通过索引和下标的方式可以吧DOM对象从jQuery的数组中选择出来

```js
	$('div')[索引]
	$('div').get(索引)
```

* 为什么以数组的方式存在呢?

  * 是因为jQuery封装之后,给DOM节点封装了很多属性和方法,

  * 如果转化为DOM就不能使用jQuery的属性和方法了

    

  **jQuery中的属性和方法  不能和js原生的方法混用, 需要使用的话需要转换**

## jQuery 元素操作

### 属性操作

* 获取jQuery 元素中的固有属性

  ```js
  语法:jq对象.prop()
  例如:$(`a`).prop(`href`) --> 获取a 的href属性
  ```

* 操作jQuery元素中的固有属性

  ```sj
  语法:jq对象.prop(`属性名`,属性值)
  ```

  

#### 操作自定义属性

* 获取自定义属性 ----> 自定义属性指的是自己需要的属性需要设置到标签内部

```js
语法: var res =  jq对象.attr(`自定义属性`) // 获取到jq对象中的自定义属性

```

* 设置自定义属性

```js
语法 : jq对象.attr(`属性值`,`属性值`);
```



#### 操作元素中的内容

* 获取设置**标签中的内容**
* 语法：

```js

    $(`a`).html()      //---> 获取标签中的所有内容，包括html标签
    $(`a`).html('值')  //---> 设置标签中的内容，包括html标签
```

总结：

> html() 相当于原生js中的  innerHtml



* 设置和获取标签中的**文本内容**

```js
    $(`a`).text()      //---> 获取标签中的所有内容，包括html标签
    $(`a`).text('值')  //---> 设置标签中的内容，包括html标签
```

总结: 

> text() 相当于原生js中的    innerText



* 设置和获取表单控件中的值

```js
     jQ对象.val()            //  ---> 获取表单控件中的值

     jQ对象.val('值')        // ---> 设置表单控件中的值
```

总结: 

> val() 相当于原生js中的    valus()

#### 小技巧

> - 可以通过jq对象,parents("选择器') 可以返回指定的先祖元素
> - **可以通过toFixed(numbe) 返回指定位数的小数,如果要保留两位小数就写2**
> - 表单控件中的值发生修改, 就会触发change事件

### 操作元素

#### 遍历元素

* 遍历元素

> 注意： jq中默认的隐式迭代只能给元素设置相同的样式，如果需要设置不同样式需要通过遍历的方式实现
>
> 语法1：
> 	jQ对象.each(function(index, domElement){ });
>
> 备注：
>    	1. 第一个参数代表每一个元素的索引值
>         2. 第二个参数代表的是一个dom对象，不是jq对象
>             3. 如果要使用jq中的方法，必须要将对象转化为jq对象

```js
语法2：
	$.each(object, function(index, element){})

备注：
   	1. object表示要遍历哪个对象，一般在程序是一个数据【数组，对象】
    2. index，表示数据的索引值
    3. element 表示数据中的值

例如：

	 //遍历程序中的数据
	 var ary = ['a','b', 'c'];
	 $.each(ary, function(i,element) {
         console.log(i, element);
     })
     //可以遍历程序中的jq对象
     $.each($('li'), function(i, element){
         console.log(i, element);
     })
	 ....
```

注意: **$.each  和  jQ对象.each 的区别使用：**

* 如果要遍历页面中的元素使用 jQ对象.each
* 如果要遍历程序中的数据使用 $.each





#### 创建元素

```js
语法:
	$('<li></li>')
```



#### 元素的位置

* 获取元素大小

| 语法                                  | 用法                                             |
| :------------------------------------ | :----------------------------------------------- |
| width() \| height()                   | 获取元素的宽度和高度                             |
| innerWidth() \| innerHeight()         | 获取元素的宽度和高度，包含padding值              |
| outerWidth()\| outerHeight()          | 获取元素的宽度和高度，包含padding值和border值    |
| outerWidth(true) \| outerHeight(true) | 获取元素的宽度和高度，包含padding，border,margin |

```js
如果以上的方法没有设置值,代表获取如果以上的值在括号内设置了,就代表修改,

```

> 注: 
>
>  **不可以带单位**

##### 获取元素的位置

* offset()

```js
语法:
	$(`a`).offset()
	$(`a`).offset({left:值,top:值}) 给当前元素设置位置
```

> 总结:
>
> 1.offset() 是用来获取当前元素距离文档的距离,与父元素无关
>
> 2.offset()返回的值为一个对象

* position()

```js
//语法
	$(`a`).position()
```

> 1.position() 返回被选中元素相对于带有定位的父级偏移坐标,如果父级元素没有定位,则追溯到body 跟绝对定位一样
>
> 2.position() 只能获取值, 不能设置

* scrollTop()   |    scrollLefl()

```js
//语法
	$(`a`).scrollTop()   //设置|返回当前元素内容区域滚出去的垂直距离
 $(`a`)scrollLeft()		//设置| 返回元素内容区域滚动(卷曲)出去的水平距离
```

> 总结: 
>
> 元素滚动事件scroll

