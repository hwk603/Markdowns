title: pandoc 转换 markdown 格式
date: 2016-03-22 17:49:47
tags: markdown
---

### 介绍

pandoc 是一个强大的文档转换工具，可实现不同标记语言间的格式转换。Pandoc使用Haskell语言编写，以命令行形式实现与用户的交互，可支持多种操作系统。

<!--more-->

### 安装

- [下载pandoc][1]
- [下载LaTeX，可以实现pdf的转换，推荐使用MikTex][2]


### 使用


##### 安装测试

安装完成以后，终端输入：`pandoc --version`，如果安装成功，会显示版本号等信息。


##### 格式转换：

- markdwon 转 docx

    ` pandoc file.md -o output.docx `
    
- markdwon 转 html

    `pandoc file.md -o output.html`
    
- markdown 转 pdf

    `pandoc file.md -o output.pdf --latex-engine=xelatex -V mainfont="Microsoft YaHei UI"`
    
    pandoc 默认选择的是 pdflatex 方式编译，pdflatex 不支持中文，因此，可以通过 `--latex-engine=xelatex` 在转换时指定 xelatex 编译方式。
    
    pandoc 默认不支持中文字体，需要添加 `-V mainfont="Microsoft YaHei UI"` 来修改默认字体为系统支持的中文字体。

    
#### 常用参数

- `–latex-engine=pdflatex|lualatex|xelatex`

    `–latex-engine` 用来指定转换PDF格式时LaTeX引擎，默认情况下是pdflatex，但是由于pdflatex不支持中文，因此需要将引擎设置为xelatex。
    
- `–template=FILE`

    使用FILE指定的文件作为输出文档的自定义模板。可将模板文件放置任意处，只是指定FILE时需要该FILE的路径。
    
- `–toc, –table-of-contents`

    使用该参数后，会在输出文档开头自动产生文件目录，对于输出格式是`man,docbook,slidy,slideous,s5,docx,odt`的文档，该参数不起任何作用。
    
- `–toc-depth=NUMBER`   

    指定文件目录中包含的章节级别，默认NUMBER=3，表示一级标题、二级标题、三级标题都会被在目录中展示。
    
- `-V KEY[=VAL], –variable=KEY[:VAL]`

    当渲染standalone模式下文档时，设置模板变量KEY的值为VAL。pandoc会自动设置默认模板中的这些变量，因此该选项这通常在使用`–template`选项指定自定义模板时有用，如果没有指定VAL值，那么该KEY会被赋予值true。
    
- `-s, –standalone`

    转换输出文档时会自动加上合适的header和footer(例如`standalone HTML, LaTeX, RTF`)。该选择在转换输出`pdf，epub，epub3，fb2，docx，odt`格式文件时会被自动设置，因此如果转换输出上述格式文件，则不用显示指定该选项。







  [1]: https://github.com/jgm/pandoc/releases/tag/1.17.0.1
  [2]: http://miktex.org/