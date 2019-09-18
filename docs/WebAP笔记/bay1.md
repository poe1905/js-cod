# DOM

* DOM - **document** object model - 文档对象模型

* **节点**：树形结构里面的每个交叉点（**标签**），被称为 `节点`  ，也叫**DOM节点**；

## 获取元素对象  Byid

* 对象: DOM节点;
* 语法: 后面需要传入元素的的 **ID** 的字符串  需要引号包括

```js
// 该方法：返回当前节点对象，也是我们在页面上看见节点
// 若是没有找到这个标签，返回为null null对象类型，代表空；

var closeBtn = document.getElementById('close');

// 获取body，因为body比较特别；永远只有一个；
document.body
```

### 获取元素对象

#### ByTagName

* 根据标签名获取元素

```js
// 参数： tagname - 标签名 - 必须是字符串
// 返回值： 一个伪数组 - 里面包含有所有满足条件的元素
// 伪数组：可以遍历；
document.getElementsByTagName(tagname);
```



#### ByClassName

* 根据元素类名获取元素

```js
// 参数： classname - 类名 - 必须是字符串
// 返回值： 一个伪数组 - 里面包含有所有满足条件的元素
// 伪数组：可以遍历；
document.getElementsByClassName(classname)
```

#### getElementsByName("")

* 获取html结构中相同**name 名称**的标签,在表单当中常用 应为多数的按钮是一个name
* 返回一个伪数组

####  获取到数组或者伪数组

*  直接使用for 循环遍历使用数组内的元素
*  因为for 是底层循环, 伪数组不可以使用forech(数组循环)

## 注册事件 

* 注册给谁: 元素对象(**DOM节点**)
* 事件? 就是用于用户交互的动作,指鼠标点击,键盘回车,本质是浏览器中的一种被触发_之后响应的一种**机制**
* 为什么要注册?   **就是为了和用户进行相互交流** .就必须给标签注册(事先声明一下,之后才可以使用,跟函数声明是一个性质,但名字不一样) , 才能和用户进行交互



### click

```js
// btn 事件源：通过谁要触发这个事件，也就是元素对象；
// click 事件类型：用户通过什么行为,去触发一件事
// 匿名函数 事件处理程序(函数)：做了这个行为之后，要做什么事情；
btn.onclick = function(){
  console.log('被点击了');
}
```

* 当事件原被点击之后就会触发这个console.log 打印属性

### focus + blur

* focus：聚焦
* blur：模糊；

* 注册给谁 : 有光标的盒子 input (文本输入框) textarea (文本域)
  * 有光标时: 获得焦点 (focus )
  * 没有光标时: 获得焦点 (blur)

```js
ipt.onfocus = function(){
  // 当你想要让鼠标光标在输入框里面的时候要做什么事，就使用这个事件即可
}

ipt.onblur =  function(){
  //当你希望处理鼠标光标失去的时候所做的事情，就在这里做
}

```



## 操作  标准属性

### 标准属性

* 操作谁?   元素对象，DOM节点； 
* **什么是标准属性?**
  * html页面内置的元素属性上面自带的 src 和class 和a 上面的href ;
  * 不通的标签都有不同的属性, 每个不同的属性都是html 编写的的时候被规定好有特殊的意义,这些属性称之为标准属性.
* **属性操作?**  我们可以通过获取到DOM 节点之后,对DOM节点以**对象**的方式管理起来
* **style 属性** 
  * style属性里面其实是多个**键值对** , js 帮我们把它们以对象的方式集合起来.
  * 获取到这些属性就可以进行操作

```js
//对象名称.样式入口.样式名称
div.style.backgroundcolor 
//打印可以打印出默认div为空值
//设置获取到就可以修改 属性 为 = "加上修改的属性"
div.style.backgroundcolor  = "#000"
```

* 可以把获取到属性和上面的点击事件联系到一块

```js
var closeBtn = document.getElementById('close');
closeBtn.onclick = function(){
  closeBtn.style.backgroundColor = ’red‘;
}
```

* 可以通过style 获取到元素的value值 

```js
closeBtn.style.value 
//修改的话就是
closeBtn.style.value = "我的新的值"
```



### 自定义属性

* 在js 当中我们程序员可以人为的给 元素节点添加属性. 属性名只要满足一定的条件就可以随意添加,属性值没有限制,
  * 属性名:   **必须 ** 在属性名之前加   **data-**(自己需要的属性名)
  * 属性值"随意"

```js
<div id="box" class="abc" title="我叫div" abc="abc" data-abc="我是自定义属性" data-index="5" data-name="狗蛋"></div>

var box = document.getElementById('box');
console.log(box.id);
console.log(box.className);
console.log(box.title);
console.log(box.abc);
console.log(box.dataset);
```

*  命名 与  获取 

```js
// 命名: 在标签上已自定义属性 以 data-属性名
<input type="button" value="美女1" data-src="./images/01.jpg" />
    
// 获取：以 data- 开头的自定义属性，都存储在了 元素.dataset 这个对象里面
ipt.dataset.src
```

* **dataset  隐藏对象**
  * 会储存通过自定义属性命名规则 之后的所有自定义命名的属性,
  * 是**伪数组**,可以**遍历**,不能使用数组遍历

```js
btn_2.onclick = function(){
  // 修改图片的src属性
  img.src= btn_2.dataset.src;
  // this，只当前事件执行的事件源本身；
  img.src= this.dataset.src;
}
```

* this 万能指   **这个**
  * 它就是指当前事件执行的事件源本身
  * 一般在for循环 中由于循环是每次附的都是值 ,无法确定每次的对象,
  * 这样用this 就可以每次循环就特指事件原本身

### 操作 类样式- className

* 操作谁: 元素对象 , DOM节点
* 类样式是什么?  是DOM节点 上的class属性  类名控制属性
* 缺点: 
  * 会直接**覆盖**掉之前的类名

```js
console.log(元素.class); // 输出undefined
console.log(元素.className); // 正常输出元素的class属性

// 如果要修改类样式，只需要把className修改一下就行了；
// 但是会直接覆盖
box.className = '新的类名';

// 解决：在原来的基础上进行添加类名
box.className += '新的类名';
```



### 操作 类样式- classList

* 操作谁?  也是 DOM节点 
* classList是什么 , 是一个**属性对象** ,管理这所有类名;
* 属性对象: 
  * 这个对象上面有多个方法可以对属性进行操作,
* add : 给元素对象 添加一个或者多个类名  不会影响原来类名
  * 不会覆盖原有类名   只是**添加** 
  * 效果只会生效  1  次

```js
// 参数：多个类名，之间用逗号隔开
box.classList.add(类名1,类名2...)；
```

* remove： 给元素删除一个或者多个类名， 
  * 如果生效过, 如果没有需要删除的类名,则不会生效第二次

```js
// 参数：多个类名，可以是多个，多个之间用逗号隔开
box.classList.remove(类名1,类名2...)
```

* toggle：切换类名
* 点击多次会生效多次,  点击一次 添加,再点击一次会消失,

```js
// 参数： 要切换的类名
box.classList.toggle(类名)
```

### 操作 标准属性-checked

* 开关属性： checked/selected/disabled ，这种只有两种状态的属性；
* 赋值：两个状态的值，布尔类型；
* 什么DOM节点时有这样的属性：`<input type="checkbox" name="check" class="ck" />

```js
var ck = document.getElementById('ck');

ck.checked = true;
ck.checked = false;
```

