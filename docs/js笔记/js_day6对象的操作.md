# 对象-数组-字符串的操作

## 内置对象

* 对象: 属性和方法的几何体: **我们关注如何使用就可以**
* 内置: js语法给我们分装好了一些对象,里面提供了很多常用,使用的属性和方法;

### Math   [ 数学 ] 

* Math.random(x) ; 这个方法的作用是生成一个[0,1)之间的**随机浮点数**

```js
var r = Math.random();
//每次执行得到的数字都不一样
```

* Math.floor(x)    把一个浮点数进行**向下取整;**    无论正负 都是向下取整

```js
console.log(Math.floor(3.1));  // 3
console.log(Math.floor(3.9));  // 3
console.log(Math.floor(-3.1)); // -4
console.log(Math.floor(-3.9)); // -4
```

* Math.round(x) 把一个浮点数进行四舍五入取整

```js
console.log(Math.round(3.1));  // 3
console.log(Math.round(3.9));  // 4
console.log(Math.round(-3.1)); // -3
console.log(Math.round(-3.9)); // -4
```

* Math.cell(x) ; 吧一个浮点数向下取整;

```js
console.log(Math.ceil(3.1));  // 4
console.log(Math.ceil(3.9));  // 4
console.log(Math.ceil(-3.1)); // -3
console.log(Math.ceil(-3.9)); // -3
```

* Math. abs (x) 求一个绝对值   正数;

```js
console.log(Math.abs(3));  // 3
console.log(Math.abs(-3)); // 3
```

* Math.max (x,y,z) ; **求多个数 的最大值** 
* Math.min (x,y,z) ; **求多个数 的最小值** 

```js
console.log(Math.max(10,20));  // 20
console.log(Math.max(8,4,5,7,3)); // 8

console.log(Math.max(10,20));  // 10
console.log(Math.max(8,4,5,7,3)); // 3
```

### Date [ 时间对象]

* 语法:

```js
var date = new Date (); // 得到的是当前时间的时间对象
```

* 获取年月日时分秒

```js
  var date = new Date();

  var 日期 = date.getDate(); 
  var 星期 = date.getDay(); 
  var 年份 = date.getFullYear(); 
  var 小时 = date.getHours();
  var 毫秒数 = date.getMilliseconds();
  var 分钟数 = date.getMinutes();
  var 月份 = date.getMonth();
  var 秒数 = date.getSeconds();
  var 从1970年到现在的毫秒数 = date.getTime();
```

![](assets\006.png)

* 时间戳
  * 获取从1970年1月1日到现在的总毫秒数.常说的**时间戳**

```js
var date = new Date();

console.log(date.valueOf());
value[ˈvæljuː ]价值/值,数值
console.log(date.getTime());
time[taɪm] 分钟、小时、年等/特指时间

console.log(1*date);//特别方法
console.log(Date.now());
```

### Aeeay   [ 数组 ]

#### 对元素操作 数组对象

* push 从数组的后面推入一个元素或者多个元素

```js
var arr = [1,2,3];

// 返回：修改后数组的长度
arr.push(4,5,6);
```

* pop 删除数组中的最后一个元素

```js
// 数组的pop方法用于将数组的最后一个元素移除
var arr = [1,2,3];

// 返回 被删除的元素；
arr.pop();
```

* unshift 从数组前面添加一个或者多个元素

```js
var arr  = [1,2,3]

//返回一个修改后数组的长度
arr.unshift ();
```

* shift 用于将数组的第一个元素移除;

```js
// 数组的shift方法用于将数组的第一个元素移除
var arr = [1,2,3];

// 返回 被删除的元素；
arr.shift(); 
```

* splice; 可以进行数组任意位置的增删改
* splice  [splaɪs]  结婚/桥接/捻接（两段绳子）
* splice   
  * 第一个值是表示从哪位**下标开始**, 
  * 第二个值是标明是**删除**多少个**元素**,
  * 第三个到之后到小括号的值都是**添加值**)
  * **注意**:这里的值是可以为表达式,或者变量;

```js
  // 数组的splice方法用于从数组的指定位置移除、添加、替换元素
  var arr = ['1', '2', '3', '4', '5'];
  // 对原数组操作
  // 作用：从下标3开始移除，总共移除1个元素 ，
  // 返回 被移除元素的数组
  arr.splice(3, 1);

  // 在c的后面添加7和8两个元素
  // 作用：从下标3开始添加，移除0个元素，把7，8加入；
  // 返回：一个空数组
  // 操作原数组；
  arr.splice(3, 0, 7, 8);
  console.log(arr);

  // 作用：从下标1开始替换，总共替换1个，用0替换 ；
  // 返回：被替换元素的数组
  arr.splice(1, 1, 0);
```

#### 数组与字符串的相互转换

* join  方法
  *  用于将数组中的多个元素以指定的分隔符链接成一个字符串

```js
  var arr = ["刘铁柱", "王大拿", "大王"];
  console.log(arr);

  arr = arr.join("**");
  console.log(arr);


  arr = arr.split("**");
  console.log(arr);

```

* split 字符串方法
  * 用于将**字符串分割**之后组成一个数组

```js
  //这个方法将一个字符串以指定的富豪分割成数组
arr = arr.split("**");
  console.log(arr);
//将输出在var 输入的内容

```

#### 查找元素

* indexOf: 方法
  * 根据䛾查找索引, 如果这个元素在数组中,返回索引,将返回 - 1 
  * 找元素在不在数组内部 

```js
var arr = [10,20,30]
console.log(arr.indexOf(30));  // 2
console.log(arr.indexOf(40));  // -1
```

* findlndex  方法 
  * 返回满足条件的元素的第一个元素的下标
  * 没有满足条件的返回一个   -1

```js

var arr = [10, 20, 30];
var res1 = arr.findIndex(function (item) {
  return item >= 20;
});
// 返回 满足条件的第一个元素的的索引
console.log(res1);  


var res2 = arr.findIndex(function (item) {
  return item >= 50;
});
// -1
console.log(res2);
```



#### 遍历数组

* for循环
* forEach :循环遍历数组

````js
  var arr = [10, 20, 30];
  arr.forEach(function(item, index, arr) {
    //----------------值的位置重要文字不重要
    //第一个位置是循环的数组元素
    //第二个位置是循环数组的下标
    //第三个位置是数组的名称(可以省略不写);
    console.log(item, index, arr);
  })
//输出:
// 10 0 (3) [10, 20, 30]
// 20 1 (3) [10, 20, 30]
// 30 2 (3) [10, 20, 30]
````

item [ˈaɪtəm  ]**项目**/一条/恋爱

index  [ˈɪndeks]  索引/指数/标志/  **在这指的是下标**



* filter 方法筛选出数组中满足条件的数组,**返回值是一个新的数组**

```js
  // 数组的filter方法用于将数组中满足条件的元素筛选出来
  // 筛选出数组中 小于 2000 的数据
  var arr_1 = [1500, 1800, 2200, 300, 2600, 800];
  // var res = arr_1.filter(function(item, index, arr) {
  //   return item > 2000;
  // });
  // fitler方法的的参数要求是一个函数，这个函数接收2个参数：item是数组中的每个元素，index是item对应的索引,arr代表当前的数组

  // 复制一个数组
var arr_2  = arr_1.filter(function (item,index) {
  return (表达式);
    //满足条件则返回哪一次的数据
})
  console.log(arr_1);
  console.log(arr_2);

```



#### 拼接与截取

* concat 方法
  * 拼接数组,不改变原数组,创建新数组
  * 返回一个新数组

```js
  // 数组的concat方法的作用是把多个数组合并成一个新的数组
  var arr1 = ["---------------"];
  var arr2 = ["++++++++++++++++"];
  var arr3 = ["==============="];
  var res = arr1.concat(arr2, arr3);
  console.log(res);
  
  // 复制一个数组
  var arr_1 = res.concat();
  console.log(arr_1);

```

* slice 截取数组:  不对原数组操作,返回是新的数组;

```js
  var arr = [21, 32, 1, 42, 41, 452, 1];
  // 表示 从下标1（包括），截取到下表为4(不包括),
  // var res = arr.slice(1, 4);

  // var arr_1 = arr.slice(1);
  // 如果不给第二个参数，默认就是把从start开始，到length结束的所有的元素截取

  // console.log(res);

  // 复制数组：如果省略两个参数，start默认是0，end默认是length
  var arr_1 = arr.slice();
  console.log(arr);
  console.log(arr_1);
```



#### 复制

```js
var  arr  = [ 10,20,30,40];
var arr_1 = [];
 arr.forEach(function(item,index,arr){
  arr_1.push (item);
})
var arr_2 = arr.filter(function(item,index,arr){
    return (item);
})


var arr_3  = arr.filter (function(item,index,arr ){
      //   // 满足条件的元素要返回
  //   // 条件成立的话（true ,false），会把满足条件的元素返回；
  //   // 直接使用的元素，隐式转化；
    return arr.indexOf(item) != -1;
}

                         
//后面不传入参数, 返回个新的数组
var arr_4 = arr.concat ();



//对数组进行操作:不输入参数,全部提取; 返回新的数组;
var arr_5 = arrslice();

```





### Object复习

* 对象是复杂类型,存储方式是 在**栈内声明地址**,在**堆中存放数据**,
* "=" 赋值号的 作用是复制一个变量的**值**到另一个变量
  * 但对象名里面存放的是指向 **堆** 的地址使用"="(赋值)号会把地址赋值给另一个变量
  * 从而不能产生一个新的对象,**只是**产生了一个指向对象的一个**变量**(内部存放着地址)
  * **总的来说**还是一个对象,不过只是有两个名字可以修改访问这个变量.

### string类型- 

#### 字符串不可变

* 字符串不可变:
  * 旧的字符串赋值在一个变量上,给变量重新赋值新的字符串(完全新的字符串,或者拼接后字符串) , 就得字符串不是被覆盖; **在内存中游离**
  * 所以尽量避免大量使用字符串的拼接,这个算性能优化的一点.

#### 查找

* indexOf 方法 
  * 查询字符
  * 返回下标 未查询到返回  -1 ;

````js
  var str = "我爱北京天安门";

  // 
  // var res = str.indexOf("天");
  // 把要查询的字符串在 整个字符串内的位置的下标反给你；
  // 查询没有的数据，返回是-1；
  // console.log(res);
````



* charAt 方法
  * 查询下标
  * 返回字符

```js

  // // 查询下标出的字符，返回字符；
  // var res_2 = str.charAt(2);
  // console.log(res_2);
```

#### 转为数组

* 字符串与数组互转(复习)

```js
 // // 把字符串转为数组；
  var str_1 = "a|b|c";
  var arr = str_1.split("|");
  console.log(arr);
  str_1 = arr.join("ABC");
  console.log(str_1);

  // // 查询的方式，从后往前查；不常用；
  // var res_1 = str.lastIndexOf("门");
  // console.log(res_1);


  // // 返回 下标出的字符的ASCII 码值；
  // var res_3 = str.charCodeAt(0);
  // console.log(res_3);
```



#### 拼接与截取

* 下面使用的方法都没有对原字符串进行操作, 返回新的字符串
* concat 方法字符串操作方法  
  * 字符串拼接

```js
  var str = "woaibeijingtiananm";
  // 1. concat 可以与多个字符串进行拼接 +
   var res = str.concat("--------", '88888');
   console.log(str, res);//生成了一个新的字符串
```

* substring方法
  * 参数为: 一个**包左不包右** 区间
  * 返回一个新的字符串
  *  // 第一个参数：**截取开始**的下标，包括
  *  // 第二个参数：**截取结束**的下标，不包括

```js
var res = str.substring(4, 11);
console.log(str, res); //返回北京---beijing
```

* slice 方法
  * 使用方法跟上面一样
  * 可以使用负值- 
  * 使用方法是吧 "-"负值与字符串长度相加得到的数字就是第一个参数

```js
  // 3.slice
  var res = str.slice(2, 9);
  console.log(str, res);
  // 其他用法, 把负值和长度进行相加


  // 其他用法：把负值和长度进行相加
  // var res = str.slice(-6, 20);
整个字符串长度为18 与-6 相加得到12 
第一个值为12 ,第二个值不变的情况下
这样slice的值为(12,20)
从第12个开始到底20个结束,不包含底20个
  
```

