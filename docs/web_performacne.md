# web Performance

## 合并多个请求 

> [Tengine ngx_http_concat_module 模块文档](http://tengine.taobao.org/document_cn/http_concat_cn.html)

```bash
# 打开的淘宝首页查看源码无意间你会发现这样加载静态资源
<script src="//g.alicdn.com/??universal/polyfill/0.0.2/p/index/index.js,mtb/lib-env/1.9.9/env.js,mtb/lib-mtop/2.5.1/mtop.js"></script>
# 浏览器的并发数是有限的，这样请求的好处就是，合并多个请求只用握手一次TCP连接，模块依赖层次比较明确
```
