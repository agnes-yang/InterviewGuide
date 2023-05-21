---
layout:  post
category:  algorithm
title:  No67、剪绳子
tagline:  by 阿秀
tags:
    - 原创
    - 剑指offer
    - 数据结构与算法
    - 算法
    - 社招
    - 校招
    - 阿秀
excerpt: No67、剪绳子
comment: false
---

<h1 align="center">带你快速刷完67道剑指offer</h1>

<div style="border-color: #24C6DC;
            background-color: #e9f9f3;         
            margin: 1rem 0;
        padding: .25rem 1rem;
        border-left-width: .3rem;
        border-left-style: solid;
        border-radius: .5rem;
        color: inherit;">
  <p>这是四则或许对你有些许帮助的信息:</p>
  <p>1、👉 最近我发现了一个每日都会推送最新校招资讯的《校招日程》文档，其中包括<a style="text-decoration: underline" href="https://flowus.cn/share/ee50d5eb-3cd5-4f74-880e-95b215dd4ff2" target="_blank">往届补录</a>、<a style="text-decoration: underline" href="https://flowus.cn/share/5f327c98-1e31-46c8-b86b-5ac6105e021f" target="_blank">应届实习校招</a>信息，比如各种大厂、国企、银行、事业编等信息都会定期更新，帮忙扩散一下。</p>  
  <p>2、😍
    免费分享阿秀个人学习计算机以来收集到的免费学习资源，<a style="text-decoration: underline" href="/notes/07-resources/01-free/01-introduce.html" target="_blank">点此白嫖</a>；也记录一下自己以前买过的<a style="text-decoration: underline" href="/notes/07-resources/02-precious.html" target="_blank">不错的计算机书籍、网络专栏和垃圾付费专栏</a>。
  </p>
  <p>3、🚀如果你想在校招中顺利拿到更好的offer，阿秀建议你多看看前人<a style="text-decoration: underline" href="https://www.yuque.com/tuobaaxiu/httmmc/npg1k81zeq4wfpyz" target="_blank">踩过的坑</a>和<a style="text-decoration: underline"  target="_blank" href="https://www.yuque.com/tuobaaxiu/httmmc/gge9ppd0mbu2d3dp">留下的经验</a>，事实上你现在遇到的大多数问题你的学长学姐师兄师姐基本都已经遇到过了。
  </p>
  <p>4、🔥 欢迎准备计算机校招的小伙伴加入我的<a  style="text-decoration: underline" href="https://www.yuque.com/tuobaaxiu/httmmc/xg0otqvc17wfx4u9" target="_blank">学习圈子</a>，一个人踽踽独行不如一群人报团取暖，圈子里沉淀了很多过去21/22/23届学长学姐的<a  style="text-decoration: underline" href="https://www.yuque.com/tuobaaxiu/httmmc/gge9ppd0mbu2d3dp" target="_blank">经验和总结</a>，好好跟着走下去的，最后基本都可以拿到不错的offer！此外，每周都会进行<a  style="text-decoration: underline" href="https://www.yuque.com/tuobaaxiu/httmmc/npg1k81zeq4wfpyz" target="_blank">精华总结和分享！</a>如果你需要《阿秀的学习笔记》网站中📚︎校招八股文相关知识点的PDF版本的话，可以<a style="text-decoration: underline" href="https://www.yuque.com/tuobaaxiu/httmmc/qs0yn66apvkzw0ps" target="_blank">点此下载</a> 。</p>   </div>

## **No67、剪绳子**

<font style="font-weight:normal; color:#4169E1;text-decoration:underline;" target="_blank">[牛客网原题链接](https://www.nowcoder.com/practice/57d85990ba5b440ab888fc72b0751bf8?tpId=13&&tqId=33257&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)</font>

### **题目描述**

给你一根长度为n的绳子，请把绳子剪成整数长的m段（m、n都是整数，n>1并且m>1），每段绳子的长度记为k[1],...,k[m]。请问k[1]x...xk[m]可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18。

**输入描述:**

```
输入一个数n，意义见题面。（2 <= n <= 60）
```

**输出描述:**

```
输出答案。
```

**示例1**

**输入**

```
8
```

**输出**

```
18
```



### **1、很厉害的一种思路**

题目分析：

 * 先举几个例子，可以看出规律来。
 * 4 ： 2*2
 * 5 ： 2*3
 * 6 ： 3*3
 * 7 ： 2\*2\*3 或者4*3
 * 8 ： 2\*3\*3
 * 9 ： 3\*3\*3
 * 10：2\*2\*3\*3 或者4\*3\*3
 * 11：2\*3\*3*3
 * 12：3\*3\*3*3
 * 13：2\*2\*3\*3\*3 或者4\*3\*3\*3

 下面是分析：
 * 首先判断k[0]到k[m]可能有哪些数字，实际上只可能是2或者3。
 * 当然也可能有4，但是4=2*2，我们就简单些不考虑了。
 * 5<2*3,6<3*3,比6更大的数字我们就更不用考虑了，肯定要继续分。
 * 其次看2和3的数量，2的数量肯定小于3个，为什么呢？因为2*2*2<3*3，那么题目就简单了。
 * 直接用n除以3，根据得到的余数判断是一个2还是两个2还是没有2就行了。
 * 由于题目规定m>1，所以2只能是1*1，3只能是2*1，这两个特殊情况直接返回就行了。
 * 乘方运算的复杂度为：O(log n)，用动态规划来做会耗时比较多。


~~~cpp
int cutRope(int number) {

	if (number == 2) {
		return 1;
	}
	if (number == 3) {
		return 2;
	}
	int x = number % 3, y = number / 3;
	if (x == 0) {
		return pow(3, y);
	}
	else if (x == 1) {
		return 2 * 2 * pow(3, y - 1);
	}
	else 
		return 2 * pow(3, y);
	
}
~~~



### **1-1、力扣上的一种讲解**

执行用时：0 ms, 在所有 C++ 提交中击败了100.00%的用户

内存消耗：6 MB, 在所有 C++ 提交中击败了100.00%的用户

~~~cpp
int cuttingRope(int n) {

    if(n<2) return 0;
    if(n<4) return n-1;
    int maxNum=1;
    while(n>4){
        maxNum*=3;
        n-=3;
    }
    maxNum*=n;
    return maxNum;
}
~~~



### **2、一种DP讲解方法**

**讲解视频：**

https://www.bilibili.com/video/BV18E411T7dU?from=search&seid=16580267998265505121

~~~cpp
int cutRope(int number) {
    if (number == 2 || number == 3)
        return number - 1;
    vector<int> ans(number + 1,0);
    ans[0] = 1;
    ans[1] = 1;
    for (int i = 2; i <= number; ++i)
    {
        ans[i] = i - 1;//分为2 段 1 * （i-1）
        for (int j = 2; j < i; ++j)
        {
            ans[i] = max(ans[i], j * ans[i - j]); //一种是继续分割的情况
            ans[i] = max(ans[i], j * (i-j));//不在分割 就割成两段
        }
    }
    return ans[number];
}
~~~



### **3、这种DP更容易懂一些**

讲解视频：https://www.bilibili.com/video/BV1C7411V7s6?from=search&seid=16580267998265505121

执行用时：0 ms, 在所有 C++ 提交中击败了100.00%的用户

内存消耗：6 MB, 在所有 C++ 提交中击败了100.00%的用户

~~~cpp
int cutRope(int number) {
    if (number < 2) return -1;
    if (number == 2 || number == 3)
        return number - 1;
    vector<int> ans(number + 1,0);
    int maxNum = -1;
    ans[1] = 1;
    ans[2] = 2;
    ans[3] = 3;//因为长度》=4，他们不需要拆，拆了反而会变小，对于小于4的情况我们直接开头处理
    for (int i = 4; i <= number; ++i)
    {
        for (int j = 1; j <= i/2; ++j)
        {
            maxNum = max(maxNum, ans[j] * ans[i - j]);
            ans[i] = maxNum;

        }

    }
    return ans[number];
}
~~~

j<=i/2 是因为 f(5) = f(1)*f(4)   f(5) = f(2)*****f(3)    f(5) = f(3)*****f(2)  

 f(5) = f(4)*****f(1)  ,可以看到走到后面去了有回来了，所以走一半即可，但一定要走到一半才行，不能小于i/2，必须是小于等于



### **二刷：**

运行时间：3ms  占用内存：508k

~~~cpp
int cutRope(int number) {
    if(number <=3 ) return number - 1;
    vector<int> dp(number+1,0);
    dp[0] = 1;
    dp[1] = 1;
    dp[2] = 2;
    dp[3] = 3;
    int maxNum = -1;
    for(int i = 4; i<= number; ++i){
        for(int j = 1; j <= i/2; ++j){
            maxNum = max(maxNum,dp[j] * dp[i-j]);
            dp[i] = maxNum;
        }
    }

    return dp[number];
}
~~~



### **剪绳子-2（力扣54题）**

给你一根长度为 n 的绳子，请把绳子剪成整数长度的 m 段（m、n都是整数，n>1并且m>1），每段绳子的长度记为 k[0],k[1]...k[m] 。

请问 k[0]\*k[1]\*...\*k[m] 可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

示例 1：
~~~
输入: 2
输出: 1
解释: 2 = 1 + 1, 1 × 1 = 1
示例 2:

输入: 10
输出: 36
解释: 10 = 3 + 3 + 4, 3 × 3 × 4 = 36


提示：

2 <= n <= 1000
~~~



### **1、DP会溢出，只能用上述规律这一种方法来做了**

执行用时：0 ms, 在所有 C++ 提交中击败了100.00%的用户

内存消耗：6.2 MB, 在所有 C++ 提交中击败了100.00%的用户

~~~cpp
int cuttingRope(int n) {
    
    if(n<2) return 0;
    if(n<4) return n-1;
    long maxNum=1,mod = 1000000007;
    while(n>4){
        maxNum*=3;
        maxNum %=mod;
        n-=3;
    }
    maxNum*=n;
    maxNum %=mod;
    return maxNum;
    }
~~~


<p id = "剪绳子"></p>

