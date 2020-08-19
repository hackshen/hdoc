# charles


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
