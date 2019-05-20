## 数组去重
ES5
```
function unique(arr) {
    const temp = []
    arr.forEach(e => {
        if (temp.indexOf(e) == -1) {
            temp.push(e)
        }
    })
    return temp
}
```
ES6
```
function unique (arr) {
   return Array.from(new Set(arr))
}
```
## 数组随机排序？
方法1
```
var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
arr.sort(function () {
    return Math.random() - 0.5;
});
```

方法2
```
var arr = [1,2,3,4,5,6,7,8,9,10];
function randSort2(arr){
    var mixedArray = [];
    while(arr.length > 0){
        var randomIndex = parseInt(Math.random()*arr.length);
        mixedArray.push(arr[randomIndex]);
        arr.splice(randomIndex, 1);
    }
    return mixedArray;
}
console.log(randSort2(arr));
```

## 数组扁平化

* 已知如下数组：var arr = [ [1, 2, 2], [3, 4, 5, 5], [6, 7, 8, 9, [11, 12, [12, 13, [14] ] ] ], 10];

* 编写一个程序将数组扁平化去并除其中重复部分数据，最终得到一个升序且不重复的数组

```
function flatten(arr) {
  let flatten = arr.toString().split(',') // flatten
  flatten = Array.from(new Set(flatten)) // make unqiue
  flatten = flatten.sort((a, b) => {
    a - b
  }) // sort the array
  return flatten
}

let arr = [1, 2, [1, 3, 4]]
console.log(flatten(arr))
```



## 实现add函数,让add(a)(b)和add(a,b)两种调用结果相同
```
function add(a, b) {
    if (b === undefined) {
        return (x) => {
            return a + x;
        }
    }
    return a + b;
}
```

## 实现一个字符串匹配算法，从长度为 n 的字符串 S 中，查找是否存在字符串 T，T 的长度是 m，若存在返回所在位置
```
const find = (S, T) => {
  if (S.length < T.length) return -1;
  for (let i = 0; i < S.length - T.length ; i++) {
      if (S.substr(i, T.length) === T) return i ;
  };
  return -1;
};
```

## 两个数组合并成一个数组
* 请把两个数组 ['A1', 'A2', 'B1', 'B2', 'C1', 'C2', 'D1', 'D2'] 和 ['A', 'B', 'C', 'D']，合并为 ['A1', 'A2', 'A', 'B1', 'B2', 'B', 'C1', 'C2', 'C', 'D1', 'D2', 'D']。

## 实现一个 sleep 函数

## 使用 sort() 对数组 [3, 15, 8, 29, 102, 22] 进行排序，输出结果


## 实现 (5).add(3).minus(2) 功能
* 例： 5 + 3 - 2，结果为 6