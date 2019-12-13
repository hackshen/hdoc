#### 解析url参数

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
