# brew 修改镜像源

```bash
# 进入brew安装目录
cd "$(brew --repo)"

# 替换源 (个人感觉比阿里云稳定)
git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git

# 更新brew
brew update

# 可以替换的源
腾讯源: https://mirrors.cloud.tencent.com/homebrew/brew.git
阿里源: https://mirrors.aliyun.com/homebrew/brew.git
清华源: https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git
```
