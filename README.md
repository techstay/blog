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

或者配置Github Action部署博客，类似如下所示的Github Action配置文件。

```
name: Deploy to Github Pages
on:
  push:
    branches: [master]
env:
  GIT_USER: techstay
  GIT_EMAIL: lovery521@gmail.com
  DEPLOY_REPO: techstay/techstay.github.io
  DEPLOY_BRANCH: gh-pages
jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: "16"
          cache: "npm"
      - name: Install Npm Dependencies
        run: npm install
      - name: Build
        run: npm run build
      - name: Configuration Environment
        env:
          HEXO_DEPLOY_KEY: ${{secrets.DEPLOY_KEY}}
        run: |
          sudo timedatectl set-timezone "Asia/Shanghai"
          mkdir -p ~/.ssh/
          echo "$HEXO_DEPLOY_KEY" > ~/.ssh/id_rsa
          chmod 600 ~/.ssh/id_rsa
          ssh-keyscan github.com >> ~/.ssh/known_hosts
          git config --global user.name $GIT_USER
          git config --global user.email $GIT_EMAIL
      - name: Deploy Hexo
        run: |
          npm run deploy
```
