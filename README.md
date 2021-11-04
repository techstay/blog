# my-static-blog

我的基于Hexo的静态博客

## 基础配置

### 安装类库

一些必须的类库。

```
npm install hexo-deployer-git --save
npm install hexo-feed --save-dev
```

## 文章编辑

### 创建新文章

```
hexo new [layout] <标题>
```

### 本地运行

```
hexo server
```

### 生成博客

```
hexo generate
```

### 部署博客

在配置文件中设置提交配置：

```
deploy:
  type: git
  repo: https://github.com/techstay/my-static-blog
  branch: gh-pages
```

然后就可以用下面的命令之一生成和提交博客了。

```
hexo generate --deploy
hexo deploy --generate
```

