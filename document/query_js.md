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

#### url

```javascript
function fromListData(shipFromList) {
    if(!shipFromList){return []}
    return shipFromList.replace('+', '').split(':').map((item)=>{
        if(item) {
            const tempObj = {};
            item.replace(/(.*?)-(.*?)([,]|$)/g, (a, b, c)=>{
                tempObj[b] = c;
            })
            return tempObj;
        }
    })
}
```

