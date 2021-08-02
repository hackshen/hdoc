# 抓包&代理

> 为什么要抓包？当你在手机上打开H5页面，你不能像浏览器那样可以打开控制台 查看资源的的请求和响应信息，且不能对不能对数据进行修改；抓包工具有很多 Charles、whistle、Flidder 等，工作需要需要目前我常用的就2个，Charles(收费的)和whistle，简单介绍下2个工具特点


## [Charles](https://www.charlesproxy.com/)

##### 主要特征
- SSL 代理– 以纯文本形式查看 SSL 请求和响应
- 带宽限制以模拟较慢的 Internet 连接，包括延迟
- AJAX 调试——以树或文本形式查看 XML 和 JSON 请求和响应
- AMF – 以树的形式查看 Flash Remoting / Flex Remoting 消息的内容
- 重复请求以测试后端更改
- 编辑请求以测试不同的输入
- 拦截和编辑请求或响应的断点
- 使用 W3C 验证器验证记录的 HTML、CSS 和 RSS/atom 响应

> Charles 是收费的软件每30min会重启一次，对于经济条件有限的可以使用 [Charles 激活码计算器](https://www.zzzmode.com/mytools/charles/) 来解决临时需要Ps: 请支持正版

### 常用功能

##### SSL Proxying Settings
- SSL Proxying: 点击Add添加规则，host和port都填`*`，这样代表抓取所有的域名和端口


##### Throttle Setting
- `Tools -> Throttle Settings`，选择Enable Throttling启用，也可以指定某个网站网速，勾选`Only for selected hosts`然后添加指定host即可

##### Compose
- 修改网络请求: 在已发送的网络请求上选择`Compose`，然后可以编辑 请求头、cookie 、url、http协议等，点击`Execute`发送请求

##### Reverse Proxies
- Charles可以允许我们进行反向代理，比如访问我们本地的81端口可以代理到，启动在别的端口上的服务

##### Map Remote
- 重定向修改响应文件的内容: 比如我们本地开发，页面请求的是 i.alicdn.com/app-name/a.js，但是我们本地的静态资源路径是127.0.0.1:8080/app-name/a.js，通过map remote 可以将远程的静态资源重定向到我们本地，方便调试开发

##### Map Local
- 重定向修改响应文件的内容: 与`Map Remote`不同的是 `Map Local`重定向到本地文件，比如你需要修改Vm模板但是 发Java应用又太慢，所以直接在本地修改DOM结构，然后通过Map Local重定向到本地的保存的DOM文件

##### Rewrite
- 对网络请求进行一些适当的修改

##### Breakpoints
- 临时修改网络一次网络请求


## [whistle](https://github.com/avwo/whistle)
> whistle(读音[ˈwɪsəl]，拼音[wēisǒu])基于Node实现的跨平台web调试代理工具，类似的工具有Windows平台上的Fiddler，主要用于查看、修改HTTP、HTTPS、Websocket的请求、响应，也可以作为HTTP代理服务器使用，不同于Fiddler通过断点修改请求响应的方式，whistle采用的是类似配置系统hosts的方式，一切操作都可以通过配置实现，支持域名、路径、正则表达式、通配符、通配路径等多种匹配方式，且可以通过Node模块扩展功

#### 如何好用

```bash
# Demo
https://assets.alicdn.com/g/ae-fe/home-msite/0.0.48/index.js  localhost:3000/index.js

# 情景一
你要和后端联调一个接口，你在本地起的项目域名是 localhost:3000 但是请求的接口是m.aliexpress.com/get/countrylist.htm, 
你本地开发调用接口势必会遇到跨域的问题，难道每次改完代码发预发验证效果么？这样效率太低了，
我们大部分的项目都是前后端分离的，所以我们直接用线上跑的页面，静态资源引用我们本地代码，一边调试一遍看效果岂不美哉，
上面的demo2就做了这样的事情，因为所有的代理都走的是whistle，whistle命中我们配置的规则会把https://assets.alicdn.com/g/ae-fe/home-msite/0.0.48/index.js 的
响应体替换为 localhost:3000/index.js，它还会帮我们设置下响应头，no-store no-chche,解决我们改完代码立即生效问题
```


#### whistle还有一个GUI版本[lightproxy](https://github.com/alibaba/lightproxy)

> LightProxy 是 IFE 团队开发的一款基于 Electron 和 whistle 的开源桌面代理软件，致力于让前端开发人员能够精确的掌握自己的开发环境，通过 HTTP 代理使用规则转发、修改每一个请求和响应的内容。

>  个人偏向于web版的whistle 搭配 [Proxy SwitchyOmega](https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif) 可自由的切换 系统代理，网页代理、直连等模式

##### 安装
```bash
npm install -g whistle

# 如果你网络不要可以指定镜像源安装
npm install whistle -g --registry=https://registry.npm.taobao.org
```

##### 使用
```bash
# 启动 whistle
w2 start

# whistle会在本地起一个web服务默认端口8899，打开web服务你会看到：
network: 经过whistle代理的一些http/s等服务
rules:  你配置的规则
```
#### [更多使用方式详见官网](http://wproxy.org/whistle/install.html)
