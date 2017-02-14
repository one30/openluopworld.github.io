---
layout: post
title: 面试问题小结
date: 2016.08.19
discription: 到目前为止，参加了一些公司的面试。本文主要对面试中遇到的一些问题做总结，为后续的面试提供一些经验...
---

到目前为止，参加了一些公司的面试。本文主要对面试中遇到的一些问题做总结，为后续的面试提供一些经验。其中一些问题来自其他同学的面试总结，如有侵权等问题，我会及时予以删除。

目前涉及到的问题都是计算机基础，比如数据结构，算法，操作系统等。

### 1. 数据结构
1. 图的存储方式
2. 红黑树的旋转操作
3. 平衡二叉树的旋转及[判断](http://zhedahht.blog.163.com/blog/static/25411174201142733927831/)

### 2. 算法
1. 二分查找的思路及代码

```C
/**
 * @purpose: binary search
 *
 * @par[a] : the ordered array
 * @par[target]　: the target value
 * @par[startIndex]　: start index of array a for the search
 * @par[endIndex] : end index of array a for the search
 *
 * @return the index if found
 *	   -1 if not found
 */
int binarySearch ( int *a, 
	int target, 
	int startIndex, 
	int endIndex ) {

	int low = startIndex;
	int high = endIndex-1;
	int mid;

	while ( low <= high ) {
		mid = (low+high)/2;
		if ( target == a[mid] ) { 
			return mid; 
		} else if ( target < a[mid] ) {
			high = mid-1;
		} else {
			low = mid+1;
		}
	}

	return -1;

}
```
2. 快速排序或桶排序的思路及代码
3. minStack:一个stack类，元素是正整数，除了push和pop之外：实现一个min函数，得到当前栈中的最小值，要求，不能对push和pop的时间复杂度有量级上的改变，min的时间复杂度尽量小；
  + 增加一个最小值数据，初始值为0；
  + push执行时，如果元素比最小值小，则更新，否则保持不变；
  + pop执行时，如果元素不是最小值，则不变，否则重新遍历查找最小值；
4. 句子中单词之间前后都有很多空格，去除句子最前面的空格，句子最后面的空格，单词之间的空格只留一个；

```C
char *temp = s;
// find the index of first word
while ( '\0' != *s && ' ' == *s++)
	NULL;
while ( '\0' != *s ) {
	if ( ' ' != *s ) {
		*temp++ = *s++;
	} else {
		*temp++ = ' ';
		s++;
		while ( '\0' != *s && ' ' == *s++)
			NULL;
	}
}
```

5. 计算f(N)，求<=N的数中，不包含4的数字个数(比如14，36248这种都是包含4的数字)；
  + 数位的个数；最高位单独作为一类，其它几位为同一类；
  + 其它位：9, 8*9=72, 8*9*9=648(900-100-8-8*9*2), 8*9*9*9;
  + 最高位不为0:3*6*3*4*8
6. N×M的矩阵中有数字0-N×M-1不重复，f(x,y)表示坐标为(x,y)的方块联通的最大面积，联通的意思是它的值比相邻的大就算联通，返回一个面积矩阵；
7. 将一个字符串a向左循环x个位置，例如，当n=8且x=3时(n为字符串有效长度)，向量abcdefgh旋转为defghabc。要求时间复杂度O(n)，空间复杂度为O(1);

```C
/**
 * The string
 * the length of string, '\0' not included
 * rotate shift left number. 0 < x < n
 */
void rrl( char * a, int n, int x ) {

	int moveIndex = 0;
	int cycles = gcd(n, x);
	char temp; // the first char
	int count;
	int i;

	for ( i = 0; i < cycles; i++ ) {
		temp = *(a+i);
		moveIndex = i;
		for ( count = 0; count < n/cycles-1; ++count ) {
			*(a+moveIndex) = *(a+(moveIndex+x)%n);
		    	moveIndex = (moveIndex + x) % n;
		}
		*(a+moveIndex) = temp;
	}
	
}
```
8. 求平面n个矩形的面积
9.　n个队列合成一个队列

### 3. 操作系统
1. 进程和线程的区别
2. grep, awt, ps命令

### 4. 语言相关
1. C语言中结构体对齐是怎么回事，为什么要对齐
2. C++中虚函数的意义
3. HashMap结构，当数据满时如何扩容
4. 一个map，能否保证数据出来的顺序和进入相同，是否有这样的map，可以如何实现


### 5. 项目相关
1. 提供API应该考虑哪些
2. 接口设计的原则
3. 如何做优化
4.　Web项目中客户端服务器的通信方式，https, socket?

### 6. 其它
1. 数据库的4种join操作
2. sql注入漏洞
3. 数据库事务
4. strcpy, memcpy的区别；strcpy，strncpy的区别
6. Singleton单例类，常见设计模式
