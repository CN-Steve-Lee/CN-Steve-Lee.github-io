---
layout: post
title:  "HOJ 1004 Prime Palindromes"
date:   2017-10-26 08:59:15
categories: HOJ
tags: 素数 回文
---

* content
{:toc}

---

# Description

The number 151 is a prime palindrome because it is both a prime number and a palindrome (it is the same number when read forward as backward). Write a program that finds all prime palindromes in the range of two supplied numbers a and b (5 <= a < b <= 1000,000,000); both a and b are considered to be within the range .

## Input

`a b`


## Output
 The list of palindromic primes in numerical order, one per line.

`palindromic primes list`
### Sample Input

    5 500  


### Sample Output    
    5
    7
    11
    101
    131
    151
    181
    191
    313
    353
    373
    383

---
# Solution

 1. 先找出范围内所有质数，再去掉不是回文的？
 2. 字符串反转相减=0
 3. 考虑边界值
 4. coding...  
 
 

# Code 

```c
#include<string.h>
#include<cstdio>
#include<algorithm>
#include<sstream>
#include<iostream>
#include<malloc.h>
using namespace std;

int main()
{
    int i,j,a,b;
    static int k=0;
    static int l=0;
	while(scanf("%d %d",&a,&b)==2){
 		int* all = (int*)malloc( b+1 );
		int* temp = (int*)malloc( b+1 );
		int* temp2 = (int*)malloc( b+1 );
	 //处理质数 
  	  for(i=a;i<b;i++){
    	for(j=2;j<i;j++){	
			if(i%j==0)
			break;
		}
		if(j>=i){
			temp[k]=i;
			k++;
		}
  	  }

  	//处理回文 
    	for(i=0;i<k;i++){
    		//int 转 string 
			stringstream ss;
			ss<<temp[i];
			
			//字符串反转 
			string m=ss.str();
    		reverse(m.begin(),m.end());
    		
    		//判断是否回文 
			int n = atoi(m.c_str()); 
			temp2[i]=n;
    	}
    	
    	for(i=0;i<k;i++){
			if((temp2[i]-temp[i])==0)
			{
				all[l]=temp[i];
				l++;
			}	
		}
		for(j=0;j<l;j++)
			cout<<all[j]<<endl;
		k=0;
		j=0;
	free(all);
	free(temp);
	}
    return 0;
 } 

```

# Summary
- 虽然思路、算法、答案都正确，但最后还是Time Limit Exceeded了，问题可能出现在翻转字符串来判定回文与否上。
- 需要用剪枝算法对判定回文和判定质数函数进行瘦身，
- 同时需要用更好的算法来求质数，当中很多数学理论和公式很有用比如黎曼猜想。
  
---
