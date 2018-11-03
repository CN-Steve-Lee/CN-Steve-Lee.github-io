---
layout: post
title:  "HOJ 1003 Mixing Milk"
date:   2017-10-25 00:59:15
categories: HOJ
tags: 排序 规划 
---

* content
{:toc}

---

# Description

Since milk packaging is such a low margin business, it is important to keep the price of the raw product (milk) as low as possible. Help Merry Milk Makers get the milk they need in the cheapest possible manner.

The Merry Milk Makers company has several farmers from which they may buy milk, and each one has a (potentially) different price at which they sell to the milk packing plant. Moreover, as a cow can only produce so much milk a day, the farmers only have so much milk to sell per day. Each day, Merry Milk Makers can purchase an integral amount of milk from each farmer, less than or equal to the farmer's limit.

Given the Merry Milk Makers' daily requirement of milk, along with the cost per gallon and amount of available milk for each farmer, calculate the minimum amount of money that it takes to fulfill the Merry Milk Makers' requirements.

Note: The total milk produced per day by the farmers will be sufficient to meet the demands of the Merry Milk Makers.




## Input

> The first line contains two integers, N and M. The first value, N, (0 <= N <= 2,000,000) is the amount of milk that Merry Milk Makers' want per day. The second, M, (0 <= M <= 	5,000) is the number of farmers that they may buy from.
The next M lines (Line 2 through M+1) each contain two integers, Pi and Ai. Pi (0 <= Pi <= 1,000) is price in cents that farmer i charges. Ai (0 <= Ai <= 2,000,000) is the amount of milk that farmer i can sell to Merry Milk Makers per day.

`N M`   

`P1 A1`   

`P2 A2`   

`·····`   

`Pn An`   


## Output
> A single line with a single integer that is the minimum price that Merry Milk Makers can get their milk at for one day.

`total `
### Sample Input

    100  5   
    5  20  
    9  40  
    3  10  
    8  80  
    6  30  


### Sample Output    
    630

---
# Solution

 1. 看起来像排序+规划问题
 2. 先对[单价-数量]中的单价进行[key-value]排序，然后每次购买后判定需求，从最低的买起并计算总价total。
 3. 考虑边界值
 4. coding...

# Code 

```c
#include<string.h>
#include<cstdio>
#include<algorithm>
#include<cstdlib>

int main()
{
    int i,j,temp1,temp2,total,M,N,A[1000],P[2000];
	total=0;
	for(i=0;i<1000;i++)
		A[i]=2000001;
	for(i=0;i<2000;i++)
		P[i]=1001;

    scanf("%d %d",&N,&M);
    for(i=0;i<M;i++)
    	scanf("%d %d",&A[i],&P[i]);
    
    for(i=0;i<M;i++){
    	for(j=0;j<M-i;j++){
	    	if(A[j]>A[j+1]){
	    		temp1=A[j];
	    		A[j]=A[j+1];
	    		A[j+1]=temp1;
	    		
	    		temp2=P[j];
	    		P[j]=P[j+1];
	    		P[j+1]=temp2;
	    	}
	    }
    }

    for(i=0;i<M;i++){
    	if(N>0){
    		if(N>P[i]){
		    	total += A[i]*P[i];
				N -= P[i];
		    }
		    else{
    			total += A[i]*N;
				N =0;
    		} 
		}
		else{
			break;
		}
    }
    printf("%d",total);
    return 0;
 } 

```

# Summary

 - 对[key-value]中的一项排序时，可用冒泡排序，用2个temp来同时同步排序。如下↓
 ```java
 for(i=0;i<M;i++){
    	for(j=0;j<M-i;j++){
	    	if(A[j]>A[j+1]){
	    		temp1=A[j];
	    		A[j]=A[j+1];
	    		A[j+1]=temp1;
	    		
	    		temp2=P[j];
	    		P[j]=P[j+1];
	    		P[j+1]=temp2;
	    	}
	    }
    }
  ```
  
---
