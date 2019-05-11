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