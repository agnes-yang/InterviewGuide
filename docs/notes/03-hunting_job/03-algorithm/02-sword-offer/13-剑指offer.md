---
layout:  post
category:  algorithm
title:  No13、调整数组顺序使奇数位于偶数前面
tagline:  by 阿秀
tags:
    - 原创
    - 剑指offer
    - 数据结构与算法
    - 算法
    - 社招
    - 校招
    - 阿秀
excerpt: No13、调整数组顺序使奇数位于偶数前面
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


## **No13、调整数组顺序使奇数位于偶数前面**

<font style="font-weight:normal; color:#4169E1;text-decoration:underline;" target="_blank">[牛客网原题链接](https://www.nowcoder.com/practice/beb5aa231adc45b2a5dcc5b62c93f593?tpId=13&&tqId=11166&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)</font>

### **题目描述**

输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有的奇数位于数组的前半部分，所有的偶数位于数组的后半部分，并保证奇数和奇数，偶数和偶数之间的相对位置不变。 



### **1、暴力解法，新开辟一个数组保存数据**

~~~cpp
void reOrderArray(vector<int>& array) {
	
	
	vector<int> temp(array.size(), 0);
	int low = 0;
	for (int i = 0; i < array.size(); ++i) {
		if ((array[i] & 1) == 1) { temp[low++] = array[i]; }
	}

	for (int i = 0; i < array.size(); ++i) {
		if ((array[i] & 1) == 0) { temp[low++] = array[i]; }
	}
	array.assign(temp.begin(), temp.end());
}
~~~



### **2、一种很巧妙的解法，空间复杂度o1的做法，时间复杂度是on^2**

~~~cpp
void reOrderArray(vector<int>& array) {
	
	for (int i = 0; i < array.size(); i++)
	{
		//for (auto a : array) {
		//	cout << a << " ";
		//}
		cout << endl;
		for (int j = array.size() - 1; j > i; j--)
		{
			if (array[j] % 2 == 1 && array[j-1] % 2 == 0) //前偶后奇就进行交换，这样一趟下来可以将第一个奇数放在首位，同时最后一个偶数放在末尾
			{
				swap(array[j], array[j - 1]);
			}
		}
	}
}
~~~



### **3、时间和空间都是on的做法，只保存偶数部分**

~~~cpp
    void reOrderArray(vector<int> &array) {
    vector<int> temp(array.size(), 0);
	int oddIndex = 0, evenIndex = 0;
	for (auto a : array) {
		if ((a & 1) == 1) array[oddIndex++] = a;
		else
			temp[evenIndex++] = a;
	}

	for (int i = 0; i < evenIndex; ++i)
		array[oddIndex + i] = temp[i];
    }
~~~



### **二刷：**

### **1、笨方法另外开辟一个数组，先保存奇数，再保存偶数**

~~~cpp
    void reOrderArray(vector<int> &array) {
        
        int len = array.size();
        if(len <= 1) return;
        int index = 0;
        vector<int> temp(len,0);
        for(int i=0;i<len;++i){
            if(array[i] %2 == 1) temp[index++] = array[i];
        }
        
       for(int i=0;i<len;++i){
            if(array[i] %2 == 0) temp[index++] = array[i];
        }
        
        array.assign(temp.begin(), temp.end());
    }
~~~



### **2、一种原地解法，很巧妙，从后向前进行修正，类似于冒泡法，同时对一刷的时候进行改进**

运行时间：2ms  占用内存：480k

~~~cpp
    void reOrderArray(vector<int> &array) {
        
	int len = array.size();
	if (len <= 1) return;
	for (int i = 0; i <= len/2; ++i) {

		for (int j = len - 1; j > i; --j) {
			if ( (array[j]&1) == 1 && (array[j - 1]&1) == 0)  swap(array[j], array[j - 1]);//前偶后奇就进行交换，并且一次就可以固定最前面的奇数位置后最后面的偶数位置，所以最多只需要遍历一般数组的长度即可，所以i<=len/2即可
		}
	}
    }
~~~



### **3、第三种解法，但是并不是原地解法，至少比第一种要好一点，只保存偶数数据**

运行时间：3ms 占用内存：484k  odd奇数：even偶数

~~~cpp
    void reOrderArray(vector<int> &array) {
        
	int len = array.size(),evenIndex = 0,oddIndex = 0;
	if (len <= 1) return;        
    vector<int> temp(len/2+1,0);
	for (int i = 0; i <len; ++i) {

		if ( (array[i]&1) == 1)  array[oddIndex++] = array[i];
        else{
            temp[evenIndex++] = array[i];//将偶数另外保存起来
        }

	}
        
    for(int j = 0;j < evenIndex; ++j){
        array[j + oddIndex] = temp[j];
    }
    }
~~~

<p id = "调整数组顺序使奇数位于偶数前面"></p>

可以维护两个下表i，j。i从数组的头开始，j从数组的尾开始。使用两个while，i从前往后找到第一个偶数，j从后往前找到第一个奇数，然后这两个数交换。重复这个过程，直到i>=j。每次都能确保i前面的数都是奇数，j后面的数都是偶数。由于i始终增大，j始终减小，时间复杂度为On，此外也不需要开辟新的空间。
