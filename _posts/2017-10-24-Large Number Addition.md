---
layout: post
title:  "HOJ 1002 A+B+C"
date:   2017-10-24 21:40:55
categories: HOJ
tags: 大数加法
---

* content
{:toc}

---

# Description

 For each pair of integers A B and C ( -2^31 <= A, B, C<= 2^31-1 ), Output the result of A+B+C on a single line.
## Input
`A B C`

## Output
`SUM` 

### Sample Input
    1 2 3
    3 4 3

### Sample Output    
    6
    10

---
# Solution

 1. 用scanf控制带格式的输入
 2. 注意题目中的ABC范围为±2^32即都是int型，所以-3x2^32≤A+B+C≤3x2^32
 3. 确定A+B+C的结果为大于int型的long int或long long int型
 4. coding...

# Code 

``` C
#include<iostream>
#include<cstdio>
int main()
{
    long long int a,b,c;
    while(scanf("%lld %lld %lld",&a,&b,&c)==3)
    {
        printf("%lld\n",a+b+c);
    }
    return 0;
 } 

```

# Summary

 - 注意边界值和每种数据类型的范围
 
---
