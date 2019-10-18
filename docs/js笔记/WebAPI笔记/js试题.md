### 遇到的有关计算的题



##### 计算类

##### 计算一个数组中重复数据的个数

例如 ["apple", "orange", "apple", "orange", "pear", "orange"]

* 问 数组中重复数据的个数

```js
  var arr = ["apple", "orange", "apple", "orange", "pear", "orange"];

  function getWordCnt1() {
    var obj = {};
    for (var i = 0; i < arr.length; i++) {
      var item = arr[i];
      obj[item] = (obj[item] + 1) || 1;
    }
    return obj;
  }
  console.log(getWordCnt1()); //{apple: 2, orange: 3, pear: 1}
  // 用reduce时： 
  var arr = ["apple", "orange", "apple", "orange", "pear", "orange"];

  function getWordCnt2() {
    return arr.reduce(function(prev, next) {
      prev[next] = (prev[next] + 1) || 1;
      return prev;
    }, {});
  }
  console.log(getWordCnt2());//{apple: 2, orange: 3, pear: 1}
```





##### 理论类

* 0.1+0.2是否等于0.3

```js
if(0.1+0.2==0.3){
   console.log("正确");
}else {
   console.log("错误");        
           
 }
```

* 在正常的数学逻辑思维中，0.1+0.2=0.3这个逻辑是正确的，但是在JavaScript中0.1+0.2！==0.3
* 在JavaScript中的二进制的浮点数0.1和0.2并不是十分精确，在他们相加的结果并非正好等于0.3，而是一个比较接近的数字 0.30000000000000004 ，所以条件判断结果为false。
* 那么应该怎样来解决0.1+0.2等于0.3呢? 最好的方法是设置一个误差范围值，通常称为”机器精度“，而对于Javascript来说，这个值通常是2^-52,而在ES6中，已经为我们提供了这样一个属性：Number.EPSILON，而这个值正等于2^-52。这个值非常非常小，在底层计算机已经帮我们运算好，并且无限接近0，但不等于0,。这个时候我们只要判断(0.1+0.2)-0.3小于Number.EPSILON，**在这个误差的范围内**就可以判定0.1+0.2===0.3为true。
* Number.EPSILON
  * EPSILON = 2^-52

```js
function numbersequal(a,b){
    return Math.abs(a-b)<Number.EPSILON;
} 
var a=0.1+0.2， b=0.3;
console.log(numbersequal(a,b)); //true
```

但是在IE10 浏览器中有兼容性问题

```js
Number.EPSILON=(function(){   //解决兼容性问题
        return Number.EPSILON?Number.EPSILON:Math.pow(2,-52);
      })();
//上面是一个自调用函数，当JS文件刚加载到内存中，就会去判断并返回一个结果，相比if(!Number.EPSILON){
  //   Number.EPSILON=Math.pow(2,-52);
  //}这种代码更节约性能，也更美观。
function numbersequal(a,b){ 
    return Math.abs(a-b)<Number.EPSILON;
  }
//接下来再判断   
    var a=0.1+0.2, b=0.3;
  console.log(numbersequal(a,b)); //这里就为true了
```



### if的简便实用方法==> &&



```js

表达式1 && 表达式2;
当表达式1 为true时会执行表达式2
当表达式1 为false
```

#### 三元表达式

```js
表达判断式1 ? 表达式2 :表达式3


表达判断式1 的返回值是 true  时会执行表达式2
表达判断式1 的返回值是 false 时会执行表达式3   
```



