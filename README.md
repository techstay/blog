# techstay.github.io ![build status](https://github.com/techstay/techstay.github.io/actions/workflows/gh-pages.yml/badge.svg)

我的静态博客站点。

## 创建项目

本项目使用hugo创建。

```sh
hugo new site techstay.github.io
cd techstay.github.io
git init
# 无需定制就直接使用主题，如果需要定制就先克隆仓库，然后自己修改
git submodule add https://github.com/techstay/hugo-theme-tokiwa.git themes/hugo-theme-tokiwa
```

## 添加文章

文章放到posts目录下。

```sh
hugo new posts/my-post.md
```

文章名以简单的中英文描述，如果遇到空格就用连字符`-`代替，详细的文件名在文章内的标题里说明。

## 本地查看

```sh
hugo server -D --bind 0.0.0.0
```

## 部署

只需正常提交代码，就可以使用Github Action自动部署。
