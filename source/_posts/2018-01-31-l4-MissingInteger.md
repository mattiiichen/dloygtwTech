---
title: Lesson 4 - MissingInteger
comments: false
toc: true
date: 2018-01-31 17:08:10
tags:
  - Codility
categories:
  - PHP
---

消失的整數。比如給一陣列，裡面找出最小正整數(大於0)，但未出現在 A 陣列中。解法：把 A 陣列的元素值用 For 迴圈放在 B 陣列的鍵上面。以及用 ksort()函數排列鍵

<!-- more -->



{% codeblock PHP的答案 lang:php http://www.writephponline.com/ PHP Online %}

function solution($A) {
    $sizeOfA = sizeof($A);
    for($i=0; $i<$sizeOfA; $i++)
        if(!isset($B[$A[$i]-1]))
            $B[$A[$i]-1] = true;
    ksort($B);
    for($i=0; $i<$sizeOfA; $i++)
        if(!isset($B[$i]))
            return $i + 1;
    return $sizeOfA + 1;
}

$A = array(1, 3, 6, 4, 5, 2);
echo solution($A);
{% endcodeblock %}	