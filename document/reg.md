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
