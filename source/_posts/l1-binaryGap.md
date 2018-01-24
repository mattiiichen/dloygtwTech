---
title: Lesson 1 - Binary Gap
date: 2018-01-19 12:08:18
tags:
  - Codility
categories:
  - PHP
comments: false
toc: true
---
>原文題目：
>A binary gap within a positive integer N is any maximal sequence of consecutive zeros that is surrounded by ones at both ends in the binary representation of N.

>For example, number 9 has binary representation 1001 and contains a binary gap of length 2. The number 529 has binary representation 1000010001 and contains two binary gaps: one of length 4 and one of length 3. The number 20 has binary representation 10100 and contains one binary gap of length 1. The number 15 has binary representation 1111 and has no binary gaps.

>Write a function:

>function solution($N);

>that, given a positive integer N, returns the length of its longest binary gap. The function should return 0 if N doesn't contain a binary gap.

>For example, given N = 1041 the function should return 5, because N has binary representation 10000010001 and so its longest binary gap is of length 5.
>Assume that:
>N is an integer within the range [1..2,147,483,647].
>Complexity:
>expected worst-case time complexity is O(log(N));
>expected worst-case space complexity is O(1).

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

切下去的左右都會取出放在陣列裡。

Answer:
{% codeblock lang:php PHP %}
function solution($N) {
    // write your code in PHP5.5
    $binary = decbin($N);
    $zero_ary = explode('1', trim($binary, '0'));
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