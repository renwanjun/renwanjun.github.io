## 命令

本地启动 `hexo s`

使用hexo-admin形式本地启动 `hexo server -d`

本地渲染 `hexo g`

发布渲染后的静态页面到GitHub `hexo d`

本地渲染和发布页面命令合并 `hexo -g d`

## 密码保护

打开localhost:4000/admin页面,打开`setting`，点击`Setup authentification here`输入用户名，密码，密钥，下面会自动生成配置文件，复制加在hexo根目录下的`_config.yml`中
```
admin:
    username:myfavoritename
    password_hash:dffdfffdfdfdf
    secret:a secret something
```

