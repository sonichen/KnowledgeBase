# MkDocs

MkDocs 是一个用于创建项目文档的 **快速**, **简单** , **完美华丽** 的静态站点生成器. 文档源码使用 Markdown 来撰写, 用一个 YAML 文件作为配置文档. 



GitHub:[https://github.com/mkdocs/mkdocs](https://wanghi.cn/go.php?https://github.com/mkdocs/mkdocs)

## Features

- Build static HTML files from Markdown files.
- Use Plugins and Markdown Extensions to enhance MkDocs.
- Use the built-in themes, third party themes or create your own.
- Publish your documentation anywhere that static files can be served.

## 安装

```
pip install mkdocs
```

```
mkdocs -h
Usage: mkdocs [OPTIONS] COMMAND [ARGS]...

  MkDocs - Project documentation with Markdown.

Options:
  -V, --version  Show the version and exit.
  -q, --quiet    Silence warnings
  -v, --verbose  Enable verbose output
  -h, --help     Show this message and exit.

Commands:
  build      Build the MkDocs documentation
  gh-deploy  Deploy your documentation to GitHub Pages
  new        Create a new MkDocs project
  serve      Run the builtin development server
```



## 创建新项目

```
mkdocs new 项目名字
```

## 运行

```
mkdocs serve
```

## 部署到GitHub 

```
mkdocs gh-deploy
```

