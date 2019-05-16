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