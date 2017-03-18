---
layout: default
---

# 面试问题小结
2016.10.17

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
*. 数据库的4种join操作
*. sql注入漏洞
*. 数据库事务
*. strcpy, memcpy的区别；strcpy，strncpy的区别
*. Singleton单例类，常见设计模式
* 给定一个长度为n的数组，编号以此为1-n；给定一个数值k，其中k>=1并且k<=n，依次让所有元素从1开始报数，报到k的元素出局，后续继续从1开始报，循环下去直至剩余一个元素。给定n和k，求最终剩下的一个元素；
* 缓冲区溢出具体是如何造成攻击的（华为）
* 白盒密码
* 公钥密码算法加密为什么比私钥密码加密慢
* RSA加密和解密速度比较
* 描述c程序从启动到执行结束的整个过程（百度）
* 滑动窗口的原理
* 以o(1)的时间复杂度实现最大栈，最小栈
* Socket的几种io模型
* strcpy与memcpy的区别与联系
* HTTPS密钥交换协议，
* double atf(char *p);实现字符串转浮点数
* 判断大尾端与小尾端
* c++的几种类型转化方式（祖龙）
* 实现LRU，要求读写时间复杂度均为O(1)，给出数据结构
* 实现strcpy函数（绿盟）
* 给定一个恶意url库，对于随时可能出现的一批请求，要求能够检测出恶意url并拒绝访问，对于正常请求则通过，对于新的恶意url添加到库中
* 实现int lengthOfLastWord(char *p);
* 握手协议，客户端与服务器断开连接的方式(正常方式以及非正常方式)
* 实现字符串转整数（商汤）
* 实现next方法，要求按中序遍历访问二叉树，时间复杂度o(1)，
* 一个长度为n的数组，元素位置固定，定义操作int max(int startIndex, int endIndex), int sum(int startIndex, int endIndex),已知上述两种操作次数很多，要求时间复杂度尽可能低。
* 已知一组url数据，共n个数据，第一列是url，第二列是点击率（介于[0,1]之间），求点击率最大的前k个url，时间复杂度为O(nlog(k))
* API调用的认证，apikey, apisecret
* 指令集的优化
* ARM处理器中SIMD
* c中动态申请内存的几种方式
* 快排时间复杂度，最坏时间复杂度，什么情况下最坏；（搜狗）
* 算法有序选择什么排序
* 函数指针，函数指针数组
* 将一个链表按奇数和偶数分为两个链表，写程序
* 求一组二维坐标上线段的长度和，可能有重叠部分，每一组数据有两个数值，分别表示起点和终点，一共n组数据；
* nginx（新浪）
* RSA基本原理
* tcp/ip建立链接过程

### Refs
1. [The Basics of C Programming](http://computer.howstuffworks.com/c.htm/printable)
2. [The Function Stack](http://www.tenouk.com/Bufferoverflowc/Bufferoverflow2a.html)
3. [A computer science portal for geeks](http://www.geeksforgeeks.org/memory-layout-of-c-program/)
4. [Anatomy of a Program in Memory](http://duartes.org/gustavo/blog/post/anatomy-of-a-program-in-memory/)
5. [How HTTPS Secures Connections: What Every Web Dev Should Know](https://blog.hartleybrody.com/https-certificates/)
6. [How does SSL/TLS work?](http://security.stackexchange.com/questions/20803/how-does-ssl-tls-work)
7. [面试精选：链表问题集锦](http://wuchong.me/blog/2014/03/25/interview-link-questions/)