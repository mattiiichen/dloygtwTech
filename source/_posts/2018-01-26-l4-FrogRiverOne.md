---
title: Lesson 4  - FrogRiverOne
comments: false
toc: true
date: 2018-01-26 12:07:01
tags:
  - Codility
categories:
  - PHP
---

一支青蛙要過河，一開始的位置在一岸 0 ，之後到對岸的位置是 x + 1。樹葉從樹上掉落在河流的水面上。給一個 A 陣列，N個整數組成來表示樹葉掉落的位置。 A[K]表示一片葉子在 K 時間掉落的位置。

<!-- more -->


最後目標是找到最短時間內，青蛙跳到河的對岸去。

給條件如下：
X = 5
和陣列 A
A[0] = 1
A[1] = 3
A[2] = 1
A[3] = 4
A[4] = 2
A[5] = 3
A[6] = 5
A[7] = 4

X和陣列 A的關係是，如兩岸長度是 5 ，那陣列裡也要有個長度為 5 ，不管幾秒。

{% codeblock PHP的答案 lang:php http://www.writephponline.com/ PHP Online %}
function solution($X, $A) {
    $check_array = array();
    for ($i = 0; $i < count($A); $i++) {
        $check_array[$i] = 0;
    }
    for ($i = 0; $i < count($A); $i++) {
        if ($check_array[$A[$i]] == 0) {
            $check_array[$A[$i]] = 1;
            $X--;
        }
        if ($X == 0) {
            return $i;
        }
    }
    return -1;
}
$A = [1, 3, 1, 4, 2, 3, 5, 4];
$X = 5;
Print_r(solution($X, $A));
{% endcodeblock %}