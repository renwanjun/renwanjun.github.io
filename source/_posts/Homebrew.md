title: Homebrew更新太慢，切换源
author: renwanjun
tags: []
categories:
  - Tool
date: 2020-02-15 15:25:00
---
执行`$ brew update`太慢，更换Homebrew的更新源。

## 更新源的选择

平时我们执行brew命令安装软件的时候，跟以下3个仓库地址有关：
+ brew.git
+ homebrew-core.git
+ homebrew-bottles

默认官方的更新源都是存放在GitHub上的，这也是中国大陆用户访问缓慢的原因，一般来说我们会更倾向选择国内提供的更新源，在此推荐中国科大以及清华大学提供的更新源,常见的还有阿里巴巴提供的更新源。
> GitHub源
+ origin https://github.com/Homebrew/brew.git
+ origin https://github.com/Homebrew/homebrew-core.git
+ origin https://github.com/Homebrew/homebrew-bottles

> 中国科大源
+ origin https://mirrors.ustc.edu.cn/brew.git
+ origin https://mirrors.ustc.edu.cn/homebrew-core.git
+ origin https://mirrors.ustc.edu.cn/homebrew-bottles

> 清华大学源
+ origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git
+ origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git
+ origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-bottles 

> 阿里巴巴源
+ origin https://mirrors.aliyun.com/homebrew/brew.git
+ origin https://mirrors.aliyun.com/homebrew/homebrew-core.git
+ origin https://mirrors.aliyun.com/homebrew/homebrew-bottles

## 替换更新源

以中国科大源为例：
```
# 替换brew.git:
$ cd "$(brew --repo)"
# 中国科大:
$ git remote set-url origin https://mirrors.ustc.edu.cn/brew.git

# 替换homebrew-core.git:
$ cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
# 中国科大:
$ git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git

# 替换homebrew-bottles:
# 中国科大:
$ echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.bash_profile
$ source ~/.bash_profile

# 应用生效:
$ brew update
```
在更新homebrew-bottles的访问地址时，与MacOS系统的shell版本有关。
查看shell版本
```
$ echo $SHELl
```

如果你的输出结果是 /bin/zsh，参考zsh 终端操作方式
```
$ echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.zshrc
$ source ~/.zshrc
```


如果你的输出结果是 /bin/bash，参考bash 终端操作方式
```
$ echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.bash_profile
$ source ~/.bash_profile
```

如果之前折腾过不少导致你的Homebrew有点问题，那么可以尝试使用如下方案：
```
# 诊断Homebrew的问题:
$ brew doctor

# 重置brew.git设置:
$ cd "$(brew --repo)"
$ git fetch
$ git reset --hard origin/master

# homebrew-core.git同理:
$ cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
$ git fetch
$ git reset --hard origin/master

# 应用生效:
$ brew update  
```
重置更新源后有时候也有换回官方GitHub源的需求
```
# 重置brew.git:
$ cd "$(brew --repo)"
$ git remote set-url origin https://github.com/Homebrew/brew.git

# 重置homebrew-core.git:
$ cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
$ git remote set-url origin https://github.com/Homebrew/homebrew-core.git
```
## 后记
1.完成更新源的更换后，我们可以使用
`$ brew upgrade`将现有的软件进行更新至最新版本，这样便能很直接的看出速度上的变化了。最后不要忘记`$ brew cleanup`将旧有的软件安装包进行清理 

2.在更新源的有时候可能会遇到上一次更新进程还没有结束的问题：
```
Error: Another active Homebrew update process is already in progress.
Please wait for it to finish or terminate it to continue.
```
使用以下命令解除homwbrew进程锁定
```
$ rm -rf /usr/local/var/homebrew/locks
```
解除锁定后再次更新

3.关闭brew每次执行命令时的自动更新，执行如下命令
```
export HOMEBREW_NO_AUTO_UPDATE=true
```
ps:如果速度还是很慢试试这个方法
[切换git代理](https://blog.csdn.net/weixin_34007886/article/details/91745327)