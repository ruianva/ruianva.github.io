
# 人人都懂Markdown

## 为什么使用markdown

- `markdown`是一组标记文档的语言，旨在将用户的精力聚焦在编辑文档的`逻辑`、`层次`内容上，而非浪费在`格式展示`、`美化排版`(这部分的工作被剥离成独立的`格式模板`由大量社区美工提供)，`markdown`几乎是所有主流IT社区撰写博客的默认语言；
- 任何`文字工作者`（尤其是`IT工程师`、`教师`、`作家`、`图书馆编辑`）都将从使用markdown中获得如下好处：

  - 基于纯文本编辑器，快速遍历检索：

  - 配合使用git/svn，可以十分方便的追溯你的编辑历史；
  - 海量精美模板，直接生成排版好的文档；
  - 开源社区开发了大量基于markdown拓展工具
    - 制作wiki手册: gitbook/docsify
    - 格式转换工具，快速导出各类格式：docx/chm/pdf/html

  

几乎所有的现代程序员编辑器(sublime/vscode/atom...)都支持markdown编写、预览；



## typora

一款免费、支持`mac`/`linux`/`windows`系统的文档编辑器；

- 逐渐取代word的功能；

  

## markdown语法

- [基础语法](https://www.jianshu.com/p/191d1e21f7ed)
- [table宽度](https://hacpai.com/article/1463381341661)

- 分段落写数字标题，因为CSS会自动处理
    - 替换已有各级标题
`(^#+ +)[\d\.]+` -> `$1`


- 引用
    由`>`开始，以两个回车作为引用结束，注意引用内容中的回车无法被识别，如果一定要有回车，使用`<br>`代替。

- 专有名词、单行代码/代码区
  - \`code\` 

  - 代码区

    ```
    ​```java
    ​```
    ```
    ```
    如css代码：
    ​```css
    table th:first-of-type {
    ​    width: 100px;
    }
    th:nth-of-type(2)
    ```

    ```
    或如java代码：
    ​```java
    System.out.println("asd")
    ```




## 格式转换

- [word插件 Writage](https://www.jianshu.com/p/df6a136d06d8)

一款office插件，安装后可直接通过F12另存为MARKDOWN插件，且表格和图片都能保存完整。

## [pandoc](https://blog.csdn.net/gyzhe/article/details/46306695)

基于命令导出docx/pdf/chm；

### 安装

[下载2.5](https://github.com/jgm/pandoc/releases)，解压后配置PATH，`pandoc -v`确认一下；

### 使用介绍

[支持转换命令范例](https://blog.csdn.net/gyzhe/article/details/46306695)

- docx->md

```shell
pandoc --extract-media ./ HD性能调优.docx -o output.md
```

- [MD->docx](https://github.com/jgm/pandoc/wiki/Pandoc-with-Chinese)

    - 导出模板进行修改

        ```
        pandoc --print-default-data-file reference.docx > reference.docx
        ```
    - 修改模板
        ```shell
        pandoc -f markdown -t docx --reference-doc reference.docx table.txt -o xxx.docx
        
        # 进行替换正则表达式
        \[.*?\]
        []
        #下载panflute panflute-1.10.6-py3-none-any.whl
        pandoc  --filter=filter2.py --reference-doc=tmplate.docx  2.3.HD配置规划.md -o markdown.docx
        ```

### Q&A

- docx->md 图片丢失问题，需要指定 `--extract-media`

- [表格样式丢失问题](https://github.com/jgm/pandoc/issues/3275)

- xelatex[不推荐]

    ```shell
    pandoc -N -s --toc --pdf-engine=xelatex -V CJKmainfont='晴圆等宽' -V mainfont='晴圆等宽' -V geometry:margin=1in markdown.md  -o output.pdf
    ```
    [table丢失](https://tex.stackexchange.com/questions/326944/tables-missing-when-i-convert-latex-file-to-html-or-docx)

    提示`xelatex not found!`
    安装`basic-miktex-2.9.6753-x64.exe`

    - everyone-> finish，update package ->amsmath 

    ```
    pandoc markdown.md  --pdf-engine=xelatex -o example13.pdf
    ```

    ```shell
    initexmf --mklinks --force
    initexmf --admin --mklinks --force
    ```
    gfm格式


```
Sub TableDefaultOptions()
  Dim tbl As Table
  For Each tbl In ActiveDocument.Tables
    tbl.ApplyStyleFirstColumn = False
    tbl.ApplyStyleLastColumn = False
    tbl.ApplyStyleLastRow = False
    tbl.ApplyStyleRowBands = True
  Next tbl
End Sub
```



- 拓展支持https://pandoc.org/MANUAL.html#markdown-variants

***
docsify/gitbook

解析md为html，提供在线预览/搜索的在线电子书；

需要通过glob.pl MarkdownBookGlob.scala递归解析目录；将结构层次目录导入README.md，

- 过滤对于非md后缀格式；

- 过滤node_modules、团队管理、_book；




- [pdf导出](https://www.princexml.com/download/)
npm config set proxy   
可以配置C:\Users\user.npmrc
registry=https://registry.npm.taobao.org 
也可以启动后刷新

### md->html

- [docsify](https://segmentfault.com/a/1190000007656679?_ea=1416350)

    - [安装](https://nodejs.org/dist/v8.11.4/node-v8.11.4-x64.msi)
    - [linux安装](https://nodejs.org/dist/v8.11.4/node-v8.11.4-linux-x64.tar.xz)
        ```shell
        tar -xJf /opt/node-v8.11.4-linux-x64.tar.xz
        ln -s /opt/node-v8.11.4-linux-x64/bin/node /usr/local/bin/node    
        ln -s /opt/node-v8.11.4-linux-x64/bin/npm /usr/local/bin/npm
        node -v
        ```
    - [点击复制](https://juejin.im/post/5afe93ab6fb9a07aa83efab7)
    - [更改MD parser](https://github.com/docsifyjs/docsify/blob/master/docs/markdown.md)
    ```shell
    npm config rm proxy
    npm config rm http-proxy
    npm config rm https-proxy
    npm config set no-proxy .huawei.com
    npm config set registry http://rnd-mirrors.huawei.com/npm-registry/
    npm i docsify-cli -g
    cd svn
    docsify init 03.交付
    docsify serve 03.交付
    nohup docsify serve . &
    ```
```shell
- npm config set registry https://registry.npmjs.org
    - https://registry.npm.taobao.org
    - http://rnd-mirrors.huawei.com/npm-registry/
    - http://r.cnpmjs.org/

npm config set proxy=http://99.1.1.144:3132
npm config set https_proxy=http://99.1.1.144:3132
npm config set proxy   
npm config set https-proxy 
npm set strict-ssl false //
```

```shell
export PATH=$PATH:/opt/node-v8.11.4-linux-x64/lib/node_modules/npm
svn checkout svn://localhost --username 
node /opt/node-v8.11.4-linux-x64/lib/node_modules/npm/node_modules/docsify-cli/bin/docsify serve .
```

正则表达式替换

# [在线编程：jupyter](https://blog.csdn.net/tryto21/article/details/80235278)

```
spip3 install jupyter
jupyter notebook --generate-config
c.NotebookApp.notebook_dir = 'D:/2.dev/jupyter'
```



# 校园IT建设

- 硬件：

  - 网络监控 sangfor，放在核心交换机前；
  - 机房/组网设计；
  - 了解设备清单；

- 图书馆/IC卡系统：

  - 浙江正远；

- 校园教务系统：

  - 管理数据库系统表结构；
  - 图书馆系统表结构；

- 教师辅助：

  - 网络备课->改卷系统；

    

  
