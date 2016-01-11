
---
layout: post
title: 约瑟夫环Joeph
date: 2015-12-25
categories: Coding
tags: [C++]
description: Python
---

###问题描述
约瑟夫（Joeph）问题的一种描述是：编号为1,2,…,n的n个人按顺时针方向围坐一圈，每人持有一个密码（正整数）。一开始任选一个正整数作为报数上限值m，从第一个人开始按顺时针方向自1开始顺序报数，报到m时停止报数。报m的人出列，将他的密码作为新的m值，从他在顺时针方向上的下一个人开始重新从1报数，如此下去，直至所有人全部出列为止。试设计一个程序求出出列顺序。
###基本要求
利用单向循环链表存储结构模拟此过程，按照出列的顺序印出各人的编号

###算法思想
游戏实现的关键是游戏信息的储存。包括玩家座位信息，玩家所报数信息以及密码信息。我们通过自定义单向循环链表Joeph_list存储结构来实现游戏过程的模拟。链表以结点连接。结点Node存储的信息包括每个人手中的密码、每个人的位置以及下一个结点在计算机中的存储位置，及指向下一个结点的指针。值得注意的是，信息“每个人的位置”是必不可少的，因为他不等同于结点在链表中的位置——但一个玩家被移除之后，链表后的元素位置会“前进”，而我们需要的玩家的位置始终是不变的。玩家的报数，我们通过循环中计数器的递增实现，当顺序递增到链表中最后一个结点，而循环仍没有结束时，我们继续从第一个元素开始递增——及相当于最后一个玩家仍没有报数到m我们就从第一个玩家重头开始报数。直到计数器累加到m，则发现我们要移除的结点，记录并输出移出结点的信息，继续游戏。直到链表中元素被清空，程序结束。算法的关键是将实际游戏场景抽象到链表中的元素的查找和移除上，要掌握清楚哪些数据代表哪些信息，并熟悉程序运行中各种判断的流程。
算法流程
![](http://upload-images.jianshu.io/upload_images/1174946-f4b5fa182b8a9b8c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
数据结构
在这个游戏中，假定每个人都是一个节点，这样有利于程序的理解。

```
template <class List_entry>  
struct Node{  
    List_entry code;             // 存储每个人手中   密码  
    List_entry iposition;        // 存储每个人所处的 位置  
    Node<List_entry> *next;  
      
    Node();  
    Node(List_entry a, List_entry b, Node<List_entry> *link=NULL);  
};  
  
template <class List_entry>  
class Joeph_list{  
    public:  
        Joeph_list();  
        int size() const;  
        bool empty() const;  
        void clear();  
          
        Error_code retrieve(int position, List_entry &x, List_entry &y) const;  
        Error_code replace(int position, const List_entry &x, const List_entry &y);  
        Error_code remove(int position, List_entry &x, List_entry &y);  
        Error_code insert(int position, const List_entry &x, const List_entry &y);  
          
        ~Joeph_list();  
    protected:  
        int count;  
        void Init();                              // 初始化线性表  
        Node<List_entry> *head;  
        Node<List_entry> *set_position(int position) const;         
 // 返回指向第position个结点的指针  
};  
```

Node结构：表示实现Joeph_list以及List表的结点
Joeph_list类：储存游戏中玩家座位、密码等信息的数据结构
List类：以链表的方式存储图片等数据结构
全局对象game：SimpleWidow的窗口输出游戏过程
List<BitMap>tu;List<BitMap>shu;List<BitMap>people;分别存储游戏参与者报数、所持密码、和游戏参与者的图片。
全局函数：

```
void Baoshu(int p,int s); 用以显示游戏参与者报数的效果
void Yizou(int p,int m); 用以移走报到数的游戏参与者
void Code(int m);  用以更新密码信息
void Jieshu(); 结束游戏
```

项目测试
1、游戏开始，初始m为6，从第一个玩家开始自动报数，报到数的人出列

2、以出列人手中的密码为密码（不大于6）继续游戏

![](http://upload-images.jianshu.io/upload_images/1174946-40947b6cd6f6a6e2.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
3、直到所有人出列，游戏结束
![](http://upload-images.jianshu.io/upload_images/1174946-4d0354f7da3a12c8.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
项目演示
[![](http://upload-images.jianshu.io/upload_images/1174946-7f508f02ad46dce2.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)](http://v.youku.com/v_show/id_XNTE1Mjk3ODgw.html)
（*点击图片可跳转到Youku视频）

代码及资料下载：[http://download.csdn.net/detail/xiaowei_cqu/5068425](http://download.csdn.net/detail/xiaowei_cqu/5068425)

分享自[xiaowei_cqu](http://blog.csdn.net/xiaowei_cqu)。