## Reg

| character | describe |
|:-:|---|
|\d | 匹配一个数字，即0-9 |
|\D | 匹配一个非数字，即除了0-9 |
|\w | 匹配一个单词字符（字母、数字、下划线） |
|\W | 匹配任何非单词字符。等价于[^A-Za-z0-9_] |
|\s | 匹配一个空白符 |
|\S | 匹配一个非空白符 |
|\b | 匹配单词边界 |
|\B | 匹配非单词边界 |
|.  | 匹配一个任意字符，除了换行符‘\n’和回车符‘\r’ |
|\1 | 重复子项 |


## Demo

#### replace
```javascript
// replace 第二个参数为函数的情况，$1为匹配到的字符，$2为分组，如果有多个分组依次增加$3,$4....
`a1b2c3dddd4`.replace(/([0-9])([a-z])/g, ($1, $2) => {
    console.log(`$1:-->` + $1, `$2:-->` + $2)
})
// 结果
// $1:-->1b $2:-->1
// $1:-->2c $2:-->2
// $1:-->3d $2:-->3
```

#### decodeHtml

```javascript
const map = {
    amp: '&',
    lt: '<',
    gt: '>',
    quot: '"',
    '#39': "'"
};

function decodeHtml(deCodeStr) {
    if (!deCodeStr) return;
    return deCodeStr.replace(/&([^;]+);/g, ($1, $2) => {
        return map[$2];
    })
}
```



```bash
parseUrl = (str)=> {
    const tempObj={}
    const parseStr = str || window.location.href.split('?')[1];
    str.replace(/(.*?)=(.*?)(&|$)/g,(a,b,c) =>{
        tempObj[b] = c;
    })
    return tempObj;
}
```
