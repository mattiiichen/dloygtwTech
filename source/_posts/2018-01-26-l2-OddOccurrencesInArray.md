---
title: Lesson 2 - OddOccurrencesInArray
comments: false
toc: true
date: 2018-01-26 14:40:43
tags:
  - Codility
categories:
  - PHP
---

發生在陣列中的奇數

<!-- more -->


一個不為空的從零索引(由多個正整數組成)，這個array 包含一個奇數個數的多元素，而且在陣列中的每一個元素都可和其中另一個元素成對，擁有相同值，只有一個元素剩下沒有成對。

N = 奇數1,3,5,7,9,11

{% codeblock PHP的答案 lang:php http://www.writephponline.com/ PHP Online %}

//If ELSE 簡寫版 echo ($value) ? ( "Yes" ) : ( "No" );
function solution($A) {
    $sizeOfA = sizeof($A);
    $hashTable = array();
    if ($sizeOfA == 1) {
        return $A[0];
    }
    for ($i = 0; $i < $sizeOfA; $i++) {
        $hashTable[$A[$i]] = empty($hashTable[$A[$i]]) ? 1 : $hashTable[$A[$i]] + 1;
        if ($hashTable[$A[$i]] == 2) {
            unset($hashTable[$A[$i]]);
        }
    }
    return key($hashTable);
}
$A = array(9, 3, 9, 3, 9, 7, 9);
echo solution($A);
{% endcodeblock %}	 