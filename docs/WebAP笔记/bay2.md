# DOM

## 获取

### 获取DOM节点

#### 使用css选择器

##### querySelector ();

* 根据指定的css选择器在html中从上到下获取第一个元素,选择器为**字符串类型**,可以使用  **id选择器**  /`类名选择器`/`属性选择器`
* 返回:  返回一找到的第一个元素 找不到就返回null

* document.querySlice All( "" ) 
  * 获取到相同选择器名字下的所有元素对象
  * 可以输入多个css选择器;
  * 返回到的是一个伪数组:可以遍历**可以forEach**

```js
document.querySelector("css选择器");
//获取document中的第一次查询到的元素对象

document.querySlice All( "css选择器" ) 

 query - 查询
 Selector - 选择器
 All - 所有，全部
	根据选择器获取

```



#### 使用ID选择

##### getElement  

* document.getElementById()
  * 获取在html内的id属性
  * 返回一个**DOM节点**
* document.getElementsByTagName()
  * 获取html内同类的名字
  * 返回一个**伪数组**/可以通过遍历/循环操作所有获取到的元素
* document.getElementsByClassName()
  * 获取到html结构中相同name名称的元素
  * 返回一个伪数组 ▲同上

```js
//根据id
document.getElementById()
//根据标签名
document.getElementsByTagName()
//根据类名
document.getElementsByClassName()
```



### 获取元素对象位置

* offset**Left** / offset**Top**

* 获取(`查询`)元素对象在   `htnl`  的位置  **不需要()**
* 返回值: 是**不带单位的数值**类型,获取到的是某个元素距离他的offsetParent元素的水平距离

```js
// 得到的是某个元素距离他的offsetParent元素的水平距离
// 元素.offsetLeft = marginLeft + left
元素.offsetLeft 
console.log(元素.offsetLeft);
//打印出来的就是一串数字
// 得到的是某个元素距离他的offsetParent元素的垂直距离
// 元素.offsetTop = marginTop + top
元素.offsetTop 

// 找到一个有定位的父亲元素进行参考，如果亲生父亲没有定位，会一直往上找，直到找打有定位的父亲，或者body；
元素.offsetParent
```



### 获取自定义属性

* 介绍
  * 使用场景:用于存储和DOM节点一一对应关系关系
  * 开发者依据自己的需要,吧数据储存到响应元素身上时使用的属性,可以自己胡乱命名:
  * 没有具体命名要求,是满足自己需求就行

#### data-开头自定义

* 语法
  * 在行内式命名的话,必须给属性名前面加上  **data-** ` name随意`

```js
<div id="box" class="father" data-abc="abc"></div>
```

* 调用
  *  必须使用dataset链接
  * 当属性自定义属性被命名过之后会储存在**隐藏dataset**对象中,需要的时候**必须先**调用dataset元素

```js
div.abc 的方式调用不出来  必须在dataset链接
console.log(div.dataset.abc, div.dataset.aaa);
```



#### 完全自定义属性

##### 介绍

* 不需要添加前缀 没有格式要求

```html
<div id="box" class="father" abc="abc"></div>
```

##### 获取

###### getAttribute

* 作用: 根据属性名获取属性名
* 参数: 要获取的属性名; 标准属性和自定义属性都可以,而且自定义属性不在限制于adta- 属性的格式要求
* 返回值: 字符串

```js
//可以获取  所有类型的属性名
box.getAttribute("可以获取到属性名");

```



###### setAttribute

* 作用:  添加或者修改值的属性
* 返回值: 字符串

```js

  // 设置: 属性名，属性值；
  box.setAttribute("abc", 456);
//会把属性名为abc属性值为456的属性添加到thml对应的元素中
```



###### removeAttribute

* 作用':删除某个元素
* 返回值: 不会返回值

```js
// 删除自定义属性：传入属性名
box.removeAttribute("abc");
```



## 事件

### 事件的三个阶段(冒泡)

* 捕获
  * 从根部忘目录DOM节点上面,一层一层的找, 捕获是用户的DOM节点
* 到达节点
* 冒泡
  * 从目标节点到根节点
  * 冒泡执行:
    * 当事件传播到某个元素身上,如果该元素也注册了同类的事件,也会执行相对应的处理程序,事件默认执行是在默认阶段
  * 阻止冒泡的发生
    * 为什么要阻止冒泡: 用户只是点击了当前的元素, 当前的元素有反应就可以了,父级元素当然不需要再执行
    * 你希望在哪里阻止:  你希望在哪里阻止, 就在哪个事件处理程序调用即可,在程序(函数)的 的前后没有要求,肯定生效.

```js
// 要阻止冒泡，需要先得到事件对象，给处理程序添加一个形参就行
uls.addEventListener("click", function (e) {
// 调用阻止事件冒泡的方法进行阻止
// 事件对象 e 把该次点击这个过程看成一个对象
e.stopPropagation();
//清除冒泡程序
//e 是元素节点(方法放在事件内部任何地方都可以)
  });
//stop [stɒp]   停止
//Propagation   传播
```



### 注册

####  on 事件

* 介绍: 
  * 本质是相当于把一个函数储存到了on这个属性后面,后面被重复赋值了,会覆盖,on的方法注册事件,不能给同一个元素进行多次少量的注册,每次注册会覆盖之前的
  * 点击事件 - click
    * 会发生在点击之后的**事件**

```js
事件源.on+事件类型 = function(事件对象){ 
   //操作 
};
```

![](assets\0001.png)

#### 事件监听

* 介绍
  * 可以获取到对象事件发生的事情或者状态

```js

事件源.addEventListener(事件类型,function(事件对象){
      //操作 
    //this 代表的是本身  "这个~~~" 
});
```



### 事件类型

* click
  * 当元素**被**单击
* focus
  * 当元素**获取**焦点
* blur
  * 当元素**失去**焦点
* mouse down
  * 当鼠标在元素上**按**下
* mouse move
  * 当鼠标在元素上**移动**
* mouse up
  * 当鼠标在元素上面**弹**起

### 解绑(注销)

* **事件注销**; 介绍
  * 
    希望曾经注册过的事件,再触发过之后,无法执行对应的事件处理程序了
  * 当事件触发的时候,把事件解绑,那么下次在此触发的时候就无效了

```js
var btn = document.getElementById('btn');
btn.addEventListener('click',function fn(){
    
  // 解绑 当前的函数
  btn.removeEventListener('click',fn);
  console.log('抽奖了');
})
// btn可以换做this 两个值("当前注册的事件",当前函数名)
//函数名必须要有,不然没法获取到自己
 btn.removeEventListener('click',fn);
```



### 委托

* **事件委托**:介绍
  * 吧事件注册到父级元素身上;
  * 利用事件冒泡执行,当事件春波到已经注册事件的父级元素身上;
  * **什么时候用? ** : 当我们需要给动态创建(不是一开始写死,是后期可能会改变)的元素实现注册事件效果的时候;
  * 理解原理



### 事件对象

* 事件对象: 根据面向对象思想,万物皆对象,吧一次事件也当做对象

* 获取事件对象

```js
获取内置
事件源.on+事件类型 = function(事件对象){   }

事件源.addEventListener(事件类型,function(事件对象){});

```



## 操作

### 属性

#### 标准属性

##### 鼠标位置

* client
  * 可视窗口为坐标系
  * clientX--X 轴  横向坐标
  * clientX--Y 轴  横向坐标

* page 
  * 页面坐标系
  * pageX    同上

**对象属性**

* target

```js
// 事件的目标对象，用户点击到谁上面了；用于事件委托；
事件对象.target
```



#### 开关属性