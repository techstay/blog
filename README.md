# techstay-blog

我的基于 hugo 的静态博客。

## 开始使用

### 安装 hugo

博客使用的主题`hugo-theme-stack`需要用到`hugo-extended`，可以通过 scoop 来安装。

```sh
scoop install hugo-extended
```

### 克隆项目

因为包含子模块，所以克隆的时候需要同时指定克隆所有子模块。

```sh
git clone --recursive git@github.com:techstay/techstay.github.io.git
```

### 添加文章

文章放到 posts 目录下。

```sh
hugo new posts/my-post.md
```

文章名以简单的英文描述，如果遇到空格就用连字符`-`代替，完整的文章标题在文章内的 front matter 里说明。因为一篇文章的标题也是经常修改的，每次同时要修改文件名和文章名挺费事的，不如直接用简短的英文描述文章主题，这样只需要修改 front matter 里的文章主题即可。比较复杂、实在没办法使用英文描述的，那就使用中文进行表达。

### 本地查看

```sh
hugo server -D --bind 0.0.0.0
```

或者直接使用`LocalRun.ps1`脚本来运行。

### 部署

使用 Cloudflare Pages 部署，正常提交代码即可。Cloudflare Pages 检测到提交后会自动执行 CI 更新页面。
