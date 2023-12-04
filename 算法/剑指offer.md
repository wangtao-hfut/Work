---
剑指offer[202312月发现牛客网上的剑指offer题库收费，特此记录]
---
---
01 数据结构
---
---
链表
---
## 1、从尾到头打印链表

**题目描述：**
输入一个链表的头节点，按链表从尾到头的顺序返回每个节点的值（用数组返回）。

如输入{1,2,3}的链表如下图:

![image](https://github.com/wangtao-hfut/Work/assets/151804453/42c3396b-5ddf-49fc-a385-bac6b4839f96)

返回一个数组为[3,2,1]

0 <= 链表长度 <= 10000

**问题分析：**

**示例代码：**
```python
# -*- coding:utf-8 -*-
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    # 返回从尾部到头部的列表值序列，例如[1,2,3]
    def printListFromTailToHead(self, listNode):
        l = [];
        head = listNode
        while listNode:
            l.insert(0,listNode.val)
            #list.insert(index, obj)函数用于将指定对象插入列表的指定位置
            #val（）函数的功能为：将一组字符型数据的数字部分转换成相应的数值型数据
            #val（）函数当识别到非数字，停止读入字符串。即如果字符串内有字母或其他非数字字符，
            #val（）函数只转换第一个非数字字符之前的数字。当字符串的首字符为非数字时，返回值为0。
            listNode = listNode.next
        return l
        
```
```java
/**
*    public class ListNode {
*        int val;
*        ListNode next = null;
*
*        ListNode(int val) {
*            this.val = val;
*        }
*    }
*
*/
import java.util.ArrayList;
public class Solution {
    public ArrayList<Integer> printListFromTailToHead(ListNode listNode) {
        ArrayList<Integer> list = new ArrayList<>();
        while(listNode!=null){
            list.add(0,listNode.val);
            listNode = listNode.next;
        }
        return list;
        
    }
}
```

## 2、反转链表

**题目描述：**
给定一个单链表的头结点pHead(该头节点是有值的，比如在下图，它的val是1)，长度为n，反转该链表后，返回新链表的表头。

数据范围： 0≤n≤1000
要求：空间复杂度 O(1) ，时间复杂度 O(n) 。

如当输入链表{1,2,3}时，
经反转后，原链表变为{3,2,1}，所以对应的输出为{3,2,1}。
以上转换过程如下图所示：
![image](https://github.com/wangtao-hfut/Work/assets/151804453/3de2dcfe-1ced-4c16-91c5-e4be685af201)
![image](https://github.com/wangtao-hfut/Work/assets/151804453/dfdb6fad-c4bb-4d82-9ce8-9040cbbc0eb7)

**问题分析：**

**示例代码：**
```java
/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}*/
public class Solution {
    public ListNode ReverseList(ListNode head) {
 //初始化pre指针，用于记录当前结点的前一个结点地址
        ListNode pre = null;
        //初始化p指针，用于记录当前结点的下一个结点地址
        ListNode p = null;
        //head指向null时，循环终止。
        while(head != null){
            //先用p指针记录当前结点的下一个结点地址。
            p = head.next;
            //让被当前结点与链表断开并指向前一个结点pre。
            head.next = pre;
            //pre指针指向当前结点
            pre = head;
            //head指向p(保存着原链表中head的下一个结点地址)
            head = p;
        }
        return pre;//当循环结束时,pre所指的就是反转链表的头结点
    }
}
```

## 3、合并两个排序的链表

**题目描述：**
输入两个递增的链表，单个链表的长度为n，合并这两个链表并使新链表中的节点仍然是递增排序的。
数据范围： 0≤n≤1000，-1000≤节点值≤1000
要求：空间复杂度 O(1)，时间复杂度 O(n)

如输入{1,3,5},{2,4,6}时，合并后的链表为{1,2,3,4,5,6}，所以对应的输出为{1,2,3,4,5,6}，转换过程如下图所示：
![image](https://github.com/wangtao-hfut/Work/assets/151804453/9a9ae485-7805-4178-be5b-5013fa1e3890)
或输入{-1,2,4},{1,3,4}时，合并后的链表为{-1,1,2,3,4,4}，所以对应的输出为{-1,1,2,3,4,4}，转换过程如下图所示：
![image](https://github.com/wangtao-hfut/Work/assets/151804453/8920d15f-98a0-4292-a66a-a5f6dfb31bd7)
![image](https://github.com/wangtao-hfut/Work/assets/151804453/60700731-b86b-4c89-ac25-342fffd1d7f7)

**问题分析：**

**示例代码：**
```Python
# -*- coding:utf-8 -*-
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution:
    # 返回合并后列表
    def Merge(self, pHead1, pHead2):
        # write code here
        if not pHead1:
            return pHead2
        if not pHead2:
            return pHead1
        if pHead1.val < pHead2.val:
            pHead1.next = self.Merge(pHead1.next, pHead2)
            return pHead1
        else:
            pHead2.next = self.Merge(pHead1, pHead2.next)
            return pHead2
```
```java
/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}*/
public class Solution {
    public ListNode Merge(ListNode list1,ListNode list2) {
        if(list1 == null ){
            return list2;
        }
        if(list2 == null){
            return list1;
        }
        if(list1 == null && list2 == null){
            return null;
        }
        //传入任意值初始化pre1，避免空指针异常。用于记录list1的前一个结点地址
        ListNode pre1 = new ListNode(-1);
        //用于记录list2的下一个结点地址
        ListNode p2 = null;
        //用于记录合并后链表的头结点。
        ListNode head = null;
        //如果list1的第一个结点值比list2第一个结点值小则用list1做表头
        if(list1.val < list2.val){
            head = list1;
        }else{
            //否则用list2做表头
            head = list2;
        }
        //当链表1和链表2都不为空时
        while(list1 != null && list2 != null){
            //如果list2的值小于等于list1则往list1前面插
            if(list2.val <= list1.val){
                p2 = list2.next;        //用p2保存list2的下一个结点
                list2.next = list1;     //把list2与list1相连
                pre1.next = list2;      //让list1的前一个结点指向list2
                pre1 = list2;           //此时list1的前一个结点变成list，更新pre1
                list2 = p2;             //list2指向下一个结点
            }else {                     //否则list1指向下一个结点
                pre1 = list1;           
                list1 = list1.next;
            }
        }
        if(list2 != null){              //插完需要判断list2是否还有值，将list2剩余值插入
            pre1.next = list2;
        }
        return head;
        
    }
}
```

## 4、两个链表的第一个公共结点

**题目描述：**
输入两个无环的单向链表，找出它们的第一个公共结点，如果没有公共节点则返回空。（注意因为传入数据是链表，所以错误测试数据的提示是用其他方式显示的，保证传入数据是正确的）

数据范围：n≤1000
要求：空间复杂度 O(1)，时间复杂度 O(n)

例如，输入{1,2,3},{4,5},{6,7}时，两个无环的单向链表的结构如下图所示：
![image](https://github.com/wangtao-hfut/Work/assets/151804453/2af28503-8675-4b96-8a8c-78a755d22325)

可以看到它们的第一个公共结点的结点值为6，所以返回结点值为6的结点。
输入描述：
输入分为是3段，第一段是第一个链表的非公共部分，第二段是第二个链表的非公共部分，第三段是第一个链表和第二个链表的公共部分。 后台会将这3个参数组装为两个链表，并将这两个链表对应的头节点传入到函数FindFirstCommonNode里面，用户得到的输入只有pHead1和pHead2。
返回值描述：
返回传入的pHead1和pHead2的第一个公共结点，后台会打印以该节点为头节点的链表。

![image](https://github.com/wangtao-hfut/Work/assets/151804453/cab8f8ad-d851-4a76-bfbf-4b9c996809f7)


**问题分析：**

**示例代码：**
```Python
# -*- coding:utf-8 -*-
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution:
    def FindFirstCommonNode(self, pHead1, pHead2):
        # write code here
        ha, hb = pHead1, pHead2
        while ha != hb:
            ha = ha.next if ha else pHead2
            hb = hb.next if hb else pHead1
        return ha
```
```java
/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}*/
public class Solution {
    public ListNode FindFirstCommonNode(ListNode pHead1, ListNode pHead2) {
 /*
链接：https://www.nowcoder.com/questionTerminal/6ab1d9a29e88450685099d45c9e31e46?answerType=1&f=discussion
来源：牛客网

双指针法。创建两个指针p1和p2,分别指向两个链表的头结点，然后依次往后遍历。如果某个指针到达末尾，则将该指针指向
另一个链表的头结点；如果两个指针所指的节点相同，则循环结束，返回当前指针指向的节点。比如两个链表分别为：
1->3->4->5->6和2->7->8->9->5->6。短链表的指针p1会先到达尾部，然后重新指向长链表头部，当长链表的
指针p2到达尾部时，重新指向短链表头部，此时p1在长链表中已经多走了k步(k为两个链表的长度差值)，
p1和p2位于同一起跑线，往后遍历找到相同节点即可。其实该方法主要就是用链表循环的方式替代了长链表指针先走k步
这一步骤。
*/
        if (pHead1 == null || pHead2 == null) return null;
            ListNode p1 = pHead1;
            ListNode p2 = pHead2;
            while (p1 != p2) {
                p1 = p1 == null ? pHead2 : p1.next;
                p2 = p2 == null ? pHead1 : p2.next;
            }
            return p1;
    }
}
```

## 5、链表中环的入口结点

**题目描述：**
给一个长度为n链表，若其中包含环，请找出该链表的环的入口结点，否则，返回null。

数据范围： n≤10000，1<=结点值<=10000
要求：空间复杂度 O(1))，时间复杂度 O(n)

例如，输入{1,2},{3,4,5}时，对应的环形链表如下图所示：

![image](https://github.com/wangtao-hfut/Work/assets/151804453/7108b2f4-a462-4477-91cc-a7800b23c79b)
可以看到环的入口结点的结点值为3，所以返回结点值为3的结点。

输入描述：

输入分为2段，第一段是入环前的链表部分，第二段是链表环的部分，后台会根据第二段是否为空将这两段组装成一个无环或者有环单链表

返回值描述：

返回链表的环的入口结点即可，我们后台程序会打印这个结点对应的结点值；若没有，则返回对应编程语言的空结点即可。



**问题分析：**

**示例代码：**
```Python
# -*- coding:utf-8 -*-
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution:
    def EntryNodeOfLoop(self, pHead):
        # write code here
        list = []
        p = pHead
        while p:
            if p in list:
                return p
            else:
                list.append(p)
            p = p.next
```



树


队列&栈

02 算法
搜索算法


动态规划

回溯

排序

位运算

模拟

其他算法
