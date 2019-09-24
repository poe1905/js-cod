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

