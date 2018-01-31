---
title: Lesson 2 - CycliRotation
comments: false
toc: true
date: 2018-01-31 16:18:38
tags:
  - Codility
categories:
  - PHP
---

圓形的旋轉，主要是將陣列中每個索引位置向右移動 K 次，位置之後怎麼變化。主要是用取餘數的概念。比如： 1 + K % $sizeofA ，直接計算無先乖除後加減。

<!-- more -->


{% codeblock PHP的答案 lang:php http://www.writephponline.com/ PHP Online %}
function solution($A, $K) {
    // write your code in PHP7.0
    
    $sizeOfA = sizeof($A);

    if($sizeOfA == 0){
        return array();
    }
    $B = array_fill(0, $sizeOfA-1, null);
    for($i=0; $i<$sizeOfA; $i++){
        $B[($i+$K)%$sizeOfA] = $A[$i];
    }
    return $B;
    
}
$A = [3, 8, 9, 7, 6];
$K = 3;
solution($A,$K);
//print_r(solution($A,$K));

{% endcodeblock %}	