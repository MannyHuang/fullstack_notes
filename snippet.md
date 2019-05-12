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

## 实现add函数,让add(a)(b)和add(a,b)两种调用结果相同
```
function add(a, b) {
    if (b === undefined) {
        return function(x) {
            return a + x
        }
    }

    return a + b
}
```