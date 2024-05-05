# NPM 



```bash
# 手动编辑npmrc
npm config edit

# 设置socks5代理
npm config set proxy='socks5://proxy.hackshen.com'

# 删除代理
npm config delete proxy

# 设置淘宝镜像
npm config set registry=https://registry.npm.taobao.org

# 设置默认镜像
npm config set registry=https://registry.npmjs.org/
```

### NPM 发布

```bash
# 添加账户
npm adduser
# 登录
npm login
# 发布
npm publish
```
### npm搭建私服

```bash
# 安装Verdaccio
npm install verdaccio -g
# verdaccio 直接运行即可
verdaccio 

# 创建账户
npm adduser --registry http://localhost:4873/
# 发布
npm publish --registry http://localhost:4873/
# 开启指定端口(默认端口: 4873)
verdaccio --listen 9999
# 指定安装源
npm install --registry http://localhost:4873
```

### NPX

```bash
# npx是一个命令行工具，它是npm 5.2.0版本中新增的功能。它允许用户在不安装全局包的情况下，运行已安装在本地项目中的包或者远程仓库中的包
# npm 和 npx区别
# npx侧重于执行命令的，执行某个模块命令。虽然会自动安装模块，但是重在执行某个命令

# npm侧重于安装或者卸载某个模块的。重在安装，并不具备执行某个模块的功能。
```
