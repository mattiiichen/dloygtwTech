---
title: Lesson 1 - BinaryGap
comments: false
toc: true
date: 2018-01-26 11:16:54
tags:
  - Codility
categories:
  - PHP
---

二進位的GAP。例如：數字 9 的二進位表示 1001。而 1001 包含 1 個 Binary Gap，並且長度為 2 。
因為 1001 頭與尾的 1 中間有兩個連續 0 。
<!--more-->

主要大意就是十進位轉二進位，Binary Gap的意思是 2 個 1 中間為零的個數有幾個。
比如說 529 的二進位是1000010001，那Binary Gap是二個，長度上分別一個是4，一個是3。
所以要求做出一個函式，傳入一個正整數的參數，回傳最大長度的Binary Gap是長度多少。

explode函數語法規則為：

{% codeblock lang:php PHP %}
explode ( string $delimiter , string $string , int $limit );
{% endcodeblock %}

PHP explode 函數有三個參數可以使用，分別解釋如下：
* $delimiter - 字串的切割處，例如在空格切開或是在某個符號切開，必填項目。
* $string - 要被切割的字串，必填項目。
* $limit -非必填項目，可以為正整數或負整數，用來限制最多可以輸出的值數量。

比如： explode("a", "aBaCaDaE");
輸出： Array ( [0] => [1] => B [2] => C [3] => D [4] => E ) NULL

切下去的左右都會取出放在陣列裡，先拿左邊的，再拿右邊，拿過的就不會再拿了。

Answer:
{% codeblock PHP的答案 lang:php http://www.writephponline.com/ PHP Online %}
function solution($N) {
    // write your code in PHP5.5
    $binary = decbin($N);   //十位進轉二位進函數
    $zero_ary = explode('1', trim($binary, '0'));//二進位數的前後要拿掉，再以 1 分割至陣列
    $max = 0;
    foreach ($zero_ary as $i => $zero_string)
    {
        if (strlen($zero_string) > $max && isset($zero_ary[$i + 1]))
        {
            $max = strlen($zero_string);
        }
    }
    return $max;
}
var_dump(solution(529));  // should be 4
var_dump(solution(1041)); // should be 5
{% endcodeblock %}