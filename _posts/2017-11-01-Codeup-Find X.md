---
layout: post
title:  "算法笔记 Find X"
date:   2017-11-01 10:40:55
categories: 算法笔记
tags: 查找 
---

* content
{:toc}


# Description
输入一个数n，然后输入n个数值各不相同，再输入一个值x，输出这个值在这个数组中的下标（从0开始，若不在数组中则输出-1）。  

## Input
测试数据有多组，输入n(1<=n<=200)，接着输入n个数，然后输入x。  
`N`  
`N1 N2 ... Nn`  
`X`  

## Output
对于每组输入,请输出结果。  





### Sample Input
    4
	1 2 3 4
	3

### Sample Output    
    2

---
# Solution

 1. 简单的查找题，遍历比较即可  


# Code 

```c++
#include<cstdio>
int main(void){
	int i,x,N=0;
	int A[200]={0};
	while(scanf("%d",&N)!=EOF){	
		for(i=0;i<N;i++)
			scanf("%d",&A[i]);
		scanf("%d",&x);
		for(i=0;i<N;i++){
			if(A[i]==x){
				printf("%d\n",i);
				break;
			}	
			if(i==N-1)
				printf("-1\n");	
		}
	}
return 0;
} 
```

# Summary

 - 注意多点测试时应该不停循环。
