---
title: DIV 水平排列
date: 2018-01-17 13:00:08
tags:
 - DIV
categories:
  - CSS
comments: false
toc: true
---

##### 如何將 6 個 DIV 變成 2 列，每列 3 個 DIV

{% asset_img div-arrangement.PNG DIV 排列 %}


{% codeblock lang:HTML HTML https://codepen.io/charisma/pen/zpmNzB CodePen %}
<div id="main--content">
  <div class="itemblock"></div>
  <div class="itemblock"></div>
  <div class="itemblock"></div>
  <div class="itemblock"></div>
  <div class="itemblock"></div>
  <div class="itemblock"></div>
</div>
{% endcodeblock %}


{% codeblock lang:CSS CSS https://codepen.io/charisma/pen/zpmNzB CodePen %}
div#main--content{
  width: 100%;
  height: 100%;
}

div#main--content div.itemblock{
  width:100px;
  height:100px;
  background-color:#9cf;
  margin:5px;
  float:left;
}
{% endcodeblock %}

有兩種方式：

{% codeblock lang:HTML HTML https://codepen.io/charisma/pen/zpmNzB CodePen %}
<!-- 將 <div style="clear:both"></div> 插入第四個位置 -->
<div id="main--content">
  <div class="itemblock"></div>
  <div class="itemblock"></div>
  <div class="itemblock"></div>
  <div style="clear:both"></div>
  <div class="itemblock"></div>
  <div class="itemblock"></div>
  <div class="itemblock"></div>
</div>
{% endcodeblock %}

{% codeblock lang:CSS CSS https://codepen.io/charisma/pen/zpmNzB CodePen %}
/* 更改寬度為 330 px; */
div#main--content{
  width: 330px;
  height: 100%;
}
{% endcodeblock %}