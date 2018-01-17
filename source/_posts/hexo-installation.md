---
title: Hexo 安裝 使用 Hipaper 主題
date: 2018-01-16 20:20:50
tags:
  - theme
categories: 
  - Hexo
comments: false
toc: true
---

相關資源：[Hexo 博客搭建指南](https://github.com/limedroid/HexoLearning)

{% codeblock %}
$ npm install hexo-cli -g
$ hexo init mattiiichen.github.io
$ cd mattiiichen.github.io
$ npm install
{% endcodeblock %}

下載主題
{% codeblock lang:yml %}
$ git clone https://github.com/iTimeTraveler/hexo-theme-hipaper.git themes/hipaper
{% endcodeblock %}

將 theme的設定更改成 hipaper
{% codeblock lang:yml %}
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: hipaper
{% endcodeblock %}


將主要 _config.yml 下的 # Deployment 配置成為自己的 Github 路徑
{% codeblock lang:yml %}
# Deployment
deploy:
  type: git
  repo: https://github.com/mattiiichen/mattiiichen.github.io.git
  branch: master
{% endcodeblock %}


使用 Hexo 指令生成 Categories 和 Tags
{% codeblock lang:yml %}
hexo new page categories
{% endcodeblock %}

之後記得把 source/categories/index.md 改成(其他目錄以此類推)
{% codeblock lang:yml %}
---
title: Categories
date: 2018-01-16 20:24:27
layout: "categories"
type: "categories"
comments: false
---
{% endcodeblock %}

