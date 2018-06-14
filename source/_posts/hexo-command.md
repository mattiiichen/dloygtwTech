---
title: Hexo 常用的指令
date: 2018-01-17 15:30:52
tags:
  - Commands
categories: 
  - Hexo
comments: false
toc: true
---

可以使用的指令
<!-- more -->
***
#### 使用指令清除、生成、啟動、怖署
{% codeblock %}
$ hexo clean
$ hexo g 
$ hexo s
$ hexo d
{% endcodeblock %}

<font style="background-color:rgba(247, 247, 12, 1)">黃色背景文字</font>

`<font style="background-color:rgba(247, 247, 12, 1)">黃色背景文字</font>`


將_config.yml文件中的配置項post_asset_folder設為true後，執行命令$ hexo new post_name，在source/_posts中會生成文章post_name.md和同名文件夾post_name。將圖片資源放在post_name中，文章就可以使用相對路徑引用圖片資源了。
{% codeblock _config.yml %}
post_asset_folder: true
{% endcodeblock %}

#### 圖片語法
在文章最上頭加入，首頁就可顯示圖片，但此方樣用在大鋼摘要圖為好，細部說明圖用另一種標簽插件語法。
{% codeblock %}
photos:
  - gallery/codeStyle01.png
{% endcodeblock %}
如果希望圖片在文章和首頁中同時顯示，可以使用標簽插件語法。
&#123;&#37; asset_img image.jpg This is an image &#37;&#125;
#### Youtube 語法
{% youtube 07sokZ0kXzY %}


#### 字型語法
斜體=*斜體*         `*斜體*`
粗體=**粗體**  `**粗體**`
粗體傾斜=***粗體傾斜***   `***粗體傾斜***`
刪除線=~~刪除線~~   `~~刪除線~~`
下劃線=__下劃線__        `__下劃線__`
下劃線斜體=__*下劃線斜體*__        `__*下劃線斜體*__`
下劃線粗體=__**下劃線粗體**__      `__**下劃線粗體**__`
下劃線粗體傾斜=__***下劃線粗體傾斜***__        `__***下劃線粗體傾斜***__`


#### 使用 Markdown Tables Generator
{% link Markdown Tables Generator網址 https://www.tablesgenerator.com/markdown_tables# %}
