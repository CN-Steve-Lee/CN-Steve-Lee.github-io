---
layout: post
title:  "算法笔记 日期处理"
date:   2017-11-2 11:40:55
categories: 算法笔记
tags: 日期 
---

* content
{:toc}


# Description
有两个日期，求两个日期之间的天数，如果两个日期是连续的我们规定他们之间的天数为两天。
## Input  
有多组数据，每组数据有两行，分别表示两个日期，形式为  
`YYYYMMDD`

## Output
每组数据输出一行，即日期差值  
`days` 





### Sample Input
    20130101
    20130105

### Sample Output    
    5

---
# Solution

 1. 首先要考虑的点有  
 	* 闰年判定
 	* 2月天数
 2. 判断日期差的思路有  
    * 直接相减计算绝对差
    * 寻找中介进行计算相对差
    * 分别统计总天数来计算日期差
    * 书上给的方法是用小日期一天天累加直至和大日期相等，然后输出flag
 3. 采用统计总天数的方法来计算两日期的插值。
 4. Coding...  

# Code 

```c++
#include<cstdio>
#include<cmath>

int isleap(int year){
	return (year%4==0&&year%100!=0)||(year%400==0)?366:365;	
}

int days(int y,int m,int d){
	int day=0;
 	int mon[13]={0,31,28,31,30,31,30,31,31,30,31,30,31};
		for(int i=1;i<y;i++)
			day+=isleap(i);
		for(int i=1;i<m;i++)
			{
				if(isleap(y)==366)
					mon[2]=29;		
				day+=mon[i];
			}
			day+=d;
		return day;
}
int main()
{
	int Date1,Date2,y1,m1,d1,y2,m2,d2,x=0;
	while(scanf("%d %d",&Date1,&Date2)!=EOF){
		y1=(int)(Date1/10000); 
		m1=((int)(Date1/100))%100;
		d1=Date1%100;
		
		y2=(int)(Date2/10000); 
		m2=((int)(Date2/100))%100;
		d2=Date2%100;
		
		x=fabs(days(y1,m1,d1)-days(y2,m2,d2))+1;
		printf("%d\n",x);
	}	
    return 0;
} 
```

# Summary
 - 判定闰年
 ```c++
bool isLeap(int year){
	return (year%4==0&&year%100!=0)||(year%400==0)?true:false;	
}
 ```
