---
title: Hexo主题安装与设置
tags:
  - Tag
categories: 
  - Hexo
---

# 主题安装
```bash
# cd you-blog dir
# 主题作者： Ruri Shimotsuki @優萌初華
# 作者blog链接： https://shoka.lostyu.me/computer-science/note/theme-shoka-doc/
git clone https://github.com/amehime/hexo-theme-shoka.git ./themes/shoka
```
# 安装依赖
Theme Shoka 依赖以下 Hexo 插件
|插件名称|npm地址|功能|依赖程度|
|:----:|:----:|:----:|:----:|
|hexo-renderer-multi-markdown-it|[链接](https://www.npmjs.com/package/hexo-renderer-multi-markdown-it)|md 文件渲染器，压缩 css/js/html|必须|
|hexo-autoprefixer|[链接](https://www.npmjs.com/package/hexo-autoprefixer)|给生成的 css 文件们添加浏览器前缀|必须|
|hexo-algoliasearch|[链接](https://www.npmjs.com/package/hexo-algoliasearch)|站内搜索功能|搜索按钮失灵|
|hexo-symbols-count-time|[链接](https://www.npmjs.com/package/hexo-symbols-count-time)|文章或站点字数及阅读时间统计|没有统计数据|
|hexo-feed|[链接](https://www.npmjs.com/package/hexo-feed)|生成 Feed 文件|feed文件没有|

:::warning
没有正确安装以上插件的话，本主题会报错 or 无法正确显示 or 部分功能失效。
hexo-renderer-multi-markdown-it 请注意升级到最新版
:::

## multi-markdown-it 安装与配置
1、安装前，记得务必卸载掉默认的 hexo-renderer-marked ，以及别的 markdown 文件渲染器.
```bash
npm un hexo-renderer-marked --save
# 或者
yarn remove hexo-renderer-marked
```
2、安装
```bash
npm i hexo-renderer-multi-markdown-it --save
# 或者
yarn add hexo-renderer-multi-markdown-it
```
3、如果安装缓慢，或者失败
```bash
ERROR: Failed to download Chromium r515411! Set "PUPPETEER_SKIP_CHROMIUM_DOWNLOAD" env variable to skip download.
```
因为有一步需要下载 puppeteer 里的 Chromium 内核，基于天朝内部网络现状，这一步能不能成功要靠科学和运气，所以为了避免安装失败，需要加上 --ignore-scripts 跳过 Chromium 内核的下载。
```bash
npm i hexo-renderer-multi-markdown-it --save --ignore-scripts
# 或者
yarn add hexo-renderer-multi-markdown-it --ignore-scripts
```
puppeteer 主要是用来渲染 mermaid 流程图，只要文章中不使用 mermaid 就没有任何问题，如果要使用 mermaid 建议还是想办法完全安装。

## 配置

### 1、加入 markdown 配置，用来渲染 md 文件
```bash
markdown:
  render: # 渲染器设置
    html: false # 过滤 HTML 标签
    xhtmlOut: true # 使用 '/' 来闭合单标签 （比如 <br />）。
    breaks: true # 转换段落里的 '\n' 到 <br>。
    linkify: true # 将类似 URL 的文本自动转换为链接。
    typographer: 
    quotes: '“”‘’'
  plugins: # markdown-it 插件设置
    - plugin:
        name: markdown-it-toc-and-anchor
        enable: true
        options: # 文章目录以及锚点应用的 class 名称，shoka 主题必须设置成这样
          tocClassName: 'toc'
          anchorClassName: 'anchor'
    - plugin:
        name: markdown-it-multimd-table
        enable: true
        options:
          multiline: true
          rowspan: true
          headerless: true
    - plugin:
        name: ./markdown-it-furigana
        enable: true
        options:
          fallbackParens: "()"
    - plugin:
        name: ./markdown-it-spoiler
        enable: true
        options:
          title: "你知道得太多了"
```
### 2、加入 minify 配置，压缩 css/js/html
```bash
minify:
  html:
    enable: true
    exclude: # 排除 hexo-feed 用到的模板文件
      - '**/json.ejs'
      - '**/atom.ejs'
      - '**/rss.ejs'
  css:
    enable: true
    exclude:
      - '**/*.min.css'
  js:
    enable: true
    mangle:
      toplevel: true
    output:
    compress:
    exclude:
      - '**/*.min.js'
```
### 3、停用默认代码高亮功能，否则代码块的 mac 样式不能正常显示。
找到 highlight 和 prismjs ，把 enable 改成 false 。
```bash
highlight:
  enable: false
prismjs:
  enable: false
```
### 4、autoprefixer 配置建议
```bash
autoprefixer:
  exclude:
    - '*.min.css'
```
缺少这个插件，首页卡片翻转效果在部分浏览器中无法正确显示。

### 5、algolia 配置建议
```bash
algolia:
  appId: #Your appId
  apiKey: #Your apiKey
  adminApiKey: #Your adminApiKey
  chunkSize: 5000
  indexName: #"shoka"
  fields:
    - title #必须配置
    - path #必须配置
    - categories #推荐配置
    - content:strip:truncate,0,2000
    - gallery
    - photos
    - tags
```
### 6、feed 配置建议
```bash
keywords: #站点关键词，用 “,” 分隔
feed:
    limit: 20
    order_by: "-date"
    tag_dir: false
    category_dir: false
    rss:
        enable: true
        template: "themes/shoka/layout/_alternate/rss.ejs"
        output: "rss.xml"
    atom:
        enable: true
        template: "themes/shoka/layout/_alternate/atom.ejs"
        output: "atom.xml"
    jsonFeed:
        enable: true
        template: "themes/shoka/layout/_alternate/json.ejs"
        output: "feed.json"
```
# 应用主题
## 修改站点配置
修改站点配置文件 <root>/_config.yml ，把主题改为 shoka
```bash
theme: shoka
```
## 修改主题配置
主题配置的所有参数在 <root>/themes/shoka/_config.yml 文件中。

为了方便主题升级，请在根目录新建一个 yml 文件，命名为 _config.shoka.yml 。
也就是说，所有主题的自定义配置均保存于 <root>/_config.shoka.yml 文件。

# 最后
再次感谢原文作者@優萌初華写的详细教程！

主题作者： Ruri Shimotsuki @優萌初華
作者blog链接： https://shoka.lostyu.me/computer-science/note/theme-shoka-doc/
