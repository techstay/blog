# techstay.github.io ![build status](https://github.com/techstay/techstay.github.io/actions/workflows/gh-pages.yml/badge.svg)

我的静态博客站点。

## 克隆项目

因为包含子模块，所以克隆的时候需要同时指定克隆所有子模块。

```sh
git clone --recursive git@github.com:techstay/techstay.github.io.git
```

## 添加文章

文章放到 posts 目录下。

```sh
hugo new posts/my-post.md
```

文章名以简单的中英文描述，如果遇到空格就用连字符`-`代替，详细的文件名在文章内的标题里说明。

## 本地查看

```sh
hugo server -D --bind 0.0.0.0
```

## 部署

只需正常提交代码，就可以使用 Github Action 自动部署。
