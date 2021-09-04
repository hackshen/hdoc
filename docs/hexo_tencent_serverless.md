# Hexo Tencent Serverless

> 利用腾讯云CloudBase服务 把Hexo的静态资源托管到腾讯云

#### 整个流程 提交代码--> 触发GitHub Action --> 安装依赖生成静态资源 --> 部署到腾讯云 --> 部署代码到master分支

#### GitHub Action 如下，参考 [搭建 Hexo](https://cloud.tencent.com/document/product/876/47006)
```yaml
name: hexo
on:
  push:
    branches: [ hexo ]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2
        with:
          ref: hexo
      - name: setNodeVersion
        uses: actions/setup-node@v1
        with:
          node-version: '8.x'
      - name: ssh
        uses: webfactory/ssh-agent@v0.5.0
        with:
          ssh-private-key: ${{ secrets.HEXO_KEY }}
      - name: npm install
        run: |
          npm install
          npx hexo g
      - name: Deploy static to Tencent CloudBase
        id: deployStatic
        uses: TencentCloudBase/cloudbase-action@v1
        with:
          # 云开发的访问密钥 secretId 和 secretKey
          secretId: ${{ secrets.SECRET_ID }}
          secretKey: ${{ secrets.SECRET_KEY }}
          # 云开发的环境id
          envId: ${{ secrets.ENV_ID }}
          # Github 项目静态文件的路径
          staticSrcPath: public
      - name: init rsync
        env:
          USE_SSH: true
          GIT_USER: hackshen
          DEPLOYMENT_BRANCH: test
        run: |
          cd ./public
          git init
          git config user.name "hackshen"
          git config user.email "hackshen.com@gmail.com"
          git add .
          git commit -m "Update docs"
          git push --force --quiet git@github.com:hackshen/hackshen.github.io.git master:master
```
