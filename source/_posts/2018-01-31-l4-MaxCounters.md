---
title: Lesson 4 - MaxCounters
comments: false
toc: true
date: 2018-01-31 20:00:26
tags:
  - Codility
categories:
  - PHP
---

找尋最大的計數器(累積的結果)  
給予 N 個計數器，並設置0，而且可以有兩個可能的操作：

1. increase(X)：將 X 的 counter加1
2. 最大化 counter - 將所有counter設置任一個其中最大值的counter

一個擁有 M 個整數的陣列 A，這陣列代表多個連續的操作。

<!-- more -->
{% codeblock PHP的答案 lang:php http://www.writephponline.com/ PHP Online %}
function solution($N, $A) {
    $max_counter = 0;
    $max_value = 0;
    $sizeOfA = sizeof($A);
    for ($i = 0; $i < $N; $i++) { //將 B 陣列初始成(0,0,0,0,0)
        $B[$i] = 0;
    }
    for ($i = 0; $i < $sizeOfA; $i++) {
        //若 A 陣列的其中元素大於 N + 1的話，就將所有元素的值變成 max_value
        if ($A[$i] > $N) {
            $max_counter = $max_value;
        } else {
            if (isset($B[$A[$i] - 1])) {
                if ($B[$A[$i] - 1] > $max_counter) $B[$A[$i] - 1] ++;
                else $B[$A[$i] - 1] = $max_counter + 1;
                if ($B[$A[$i] - 1] > $max_value) $max_value = $B[$A[$i] - 1];//更新最大的值
            }
        }
        // var_dump($max_counter);
        //var_dump($max_value);
        // var_dump($B);
        // print_r($B);
    }
    //    var_dump($B);
    for ($i = 0; $i < $N; $i++) {
        if ($B[$i] < $max_counter) $B[$i] = $max_counter;
    }
    //    var_dump($B);
    return $B;
}
$N = 5;
$A = array(3, 4, 4, 6, 1, 4, 4);
echo "<pre>".print_r(solution($N, $A), true)."</pre>";
//print_r(solution($N,$A));
{% endcodeblock %}	


|  B陣列 | 0 | 0 | 0 | 0 | 0 | Max_Counter | Max_Value |
|:------:|:-:|:-:|:-:|:-:|:-:|:-----------:|:---------:|
|        | 0 | 0 | 0 | 0 | 0 |      0      |     0     |
|   A3   | 0 | 0 | 1 | 0 | 0 |      0      |     1     |
|   A4   | 0 | 0 | 1 | 1 | 0 |      0      |     1     |
|   A4   | 0 | 0 | 1 | 2 | 0 |      0      |     2     |
|   A6   | 0 | 0 | 1 | 2 | 0 |      2      |     2     |
|   A1   | 3 | 0 | 1 | 2 | 0 |      2      |     3     |
|   A4   | 3 | 0 | 1 | 3 | 0 |      2      |     3     |
|   A4   | 3 | 0 | 1 | 4 | 0 |      2      |     4     |
| Result | 3 | 2 | 2 | 4 | 2 |             |           |