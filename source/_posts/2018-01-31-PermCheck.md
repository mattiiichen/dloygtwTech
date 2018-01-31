---
title: Lesson 4 - PermCheck
comments: false
toc: true
date: 2018-01-31 16:32:34
tags:
  - Codility
categories:
  - PHP
---

Permutation 是可排列之意。此題是檢查陣列的元素是否可排成數列。可排列回傳 1 ，不可排列回傳 0。

<!-- more -->




{% codeblock PHP的答案 lang:php http://www.writephponline.com/ PHP Online %}

function solution($A) {
    $sizeOfA = sizeof($A);
    //若條件陣列某元素的值重覆或是值大於陣列總數或是值小於 1 ，就回傳 0。
    for($i=0; $i<$sizeOfA; $i++){
        if( isset($solution[$A[$i]]) || $A[$i] > $sizeOfA || $A[$i] < 1 ){
            return 0;
        }else{
            $solution[$A[$i]] = true;
        }
    }
    return 1;
}
solution($A);
{% endcodeblock %}	