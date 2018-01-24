---
title: frogRiverOne
date: 2018-01-20 11:03:08
tags:
  - Codility
categories:
  - PHP
comments: false
toc: true
---

Answer:

{% codeblock lang:php PHP %}
function solution($X, $A)
	{
	$check_array = array();
	for ($i = 0; $i < count($A); $i++)
		{
		$check_array[$i] = 0;
		}
	for ($i = 0; $i < count($A); $i++)
		{
		if ($check_array[$A[$i]] == 0)
			{
			$check_array[$A[$i]] = 1;
			$X--;
			}
		if ($X == 0)
			{
			return $i;
			}
		}
	return -1;
	}
$A = [1, 3, 1, 4, 2, 3, 5, 4];
$X = 5;
Print_r(solution($X, $A));
{% endcodeblock %}