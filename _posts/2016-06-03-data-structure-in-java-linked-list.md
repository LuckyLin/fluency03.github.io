---
title: "Data Structure in Java: Linked List | Java 数据结构: 链表"
layout: post
date: 2016-06-03 22:25
tag:
- Data Structure
- Java
- Linked List
- Programming
blog: true
---

In computer science, **Linked List** is probably one of the most simple but commonly used data stucture. It is consisting of a group of nodes linked together representing an ordered linear sequence. The nodes are pointing to their next node by means of a pointer or so-called link. Under the simplest form, each node is composed of the data payload and a reference (in other words, a link) to the next node on the sequence; more complex variants add additional links or dummy data.

This linked structure allows for efficient operations of insertion and removal of elements at any position on the sequence, which can be as quick as with time complexity O(1). This is the principal benefit of a linked list over a conventional array, which can avoid the reallocation or reorganization of the entire structure because the data items are not stored contiguously in memory or on disk, while an array has to be declared in the source code, before compiling and running the program. The last node is linked to a terminator used to signify the end of the list.

Howver, simple linked lists by themselves do not allow random access to the data, or any form of efficient indexing. Thus, many basic operations — such as obtaining the last node of the list (assuming that, the last node is not maintained as separate node reference in the list structure, nor it is not a doubly linked list), or finding a node that contains a given data payload, or locating the place where a new node should be inserted — may require sequential scanning of most or even all of the list elements.

As the most basic data structure, linked list can also be used to implement other common abstract data types, including lists (the abstract data type), stacks, queues, associative arrays (maps or dictionaries), though it is not uncommon to implement the other data structures directly without using a list as the basis of implementation.

The advantages and disadvantages of using linked lists are given below.

### Advantages

* Linked lists are a dynamic data structure, which can grow and be pruned, allocating and deallocating memory while the program is running.


* Nodes insertion and deletion operations can be easily implemented in a linked list and only with O(1) time. There are some additional tricks should be done for O(1) time operation.


* Linear data structures such as stacks and queues can be easily constructed and executed with a linked list.


* They can reduce access time and may expand in real time without memory overhead.



### Disadvantages

* More memory requried than arrays because of the storage used by the links pointing to other nodes.


* Node cannot be directly searched and accessed within a O(1) time, which must be read in order from the beginning as linked lists are inherently sequential access. This leads to the worst time compexity as O(n), where n is the number of nodes on the list. However, the data of array can be addressed with O(1) time because of direct indexing.


* Nodes are stored incontiguously, greatly increasing the time required to access individual elements within the list.


* Difficulties arise in linked lists when it comes to reverse traversing. For instance, singly linked lists are cumbersome to navigate backwards and while doubly linked lists are somewhat easier to read, memory is wasted in allocating space for a back pointer.



### List Node

The following code is for the singly linked **ListNode**:


<script src="https://gist.github.com/fluency03/5e472e83fe72720f37fea9bafd355ec7.js"></script>


### Singly linked list

![Singly linked list][4]
<figcaption class="caption">Singly Linked List</figcaption>


### Doubly linked list

![Doubly linked list][5]
<figcaption class="caption">Doubly Linked List</figcaption>


### Circular linked list

![Circular linked list][6]
<figcaption class="caption">Circular (Singly) Linked List</figcaption>


### Sentinel nodes

Sentinel node (or dummy node) is a specifically designated node for linked list (or some other data strutures such as tree) as a traversal path terminator. This type of node does not hold or reference any data managed by the data structure, instead, it normally contains certain meanless payload such as *Null*, *Infinity* or *Dummy*.

Sentinel node can simplify certain list operations (such as efficient node deleting), by ensuring that the next or previous nodes must exist for every element, and that even empty lists have at least one node. One may also use a sentinel node at the end of the list, with an appropriate data field, to eliminate some end-of-list tests. However, sentinel nodes use up extra space (especially in applications that may require many short lists), and they may complicate some other operations (such as the creation of a new empty list).

<!-- However, if the circular list is used merely to simulate a linear list, one may avoid some of this complexity by adding a single sentinel node to every list, between the last and the first data nodes. With this convention, an empty list consists of the sentinel node alone, pointing to itself via the next-node link. The list handle should then be a pointer to the last data node, before the sentinel, if the list is not empty; or to the sentinel itself, if the list is empty. -->

<!-- The same trick can be used to simplify the handling of a doubly linked linear list, by turning it into a circular doubly linked list with a single sentinel node. However, in this case, the handle should be a single pointer to the dummy node itself. -->


<!-- Sentinels are used as an alternative over using null as the path terminator in order to get one or more of the following benefits: -->

Benifits:

* Increased efficy and speed of certain list operations
* Reduced algorithmic complexity and code size
* Increased data structure robustness (arguably)


### TODO: Interview Questions

1. Delete a node with time complexity of O(1) \| 在O(1)时间删除链表节点

   题目描述：给定链表的头指针和一个节点指针，在O(1)时间删除该节点。[Google面试题]

2. Reverse of a singly linked list \| 单链表的转置

   题目描述：输入一个单向链表，输出逆序反转后的链表。

3. The kth node from the end \| 求链表倒数第k个节点

   题目描述：输入一个单向链表，输出该链表中倒数第k个节点，链表的倒数第0个节点为链表的尾指针。

4. Get the middle node of the linked list \| 求链表的中间节点

   题目描述：求链表的中间节点，如果链表的长度为偶数，返回中间两个节点的任意一个，若为奇数，则返回中间节点。

5. Check whether there is a loop \| 判断单链表是否存在环

   题目描述：输入一个单向链表，判断链表是否有环？

6. Find the entry of a loop \| 找到环的入口点

   题目描述：输入一个单向链表，判断链表是否有环。如果链表存在环，如何找到环的入口点？

7. Check whether two linked list are merged at some point \| 编程判断两个链表是否相交

   题目描述：给出两个单向链表的头指针（如下图所示）

   ![Merged Linked List][1]

   比如h1、h2，判断这两个链表是否相交。这里为了简化问题，我们假设两个链表均不带环。

8. What if the linked list contains loop for above question 7 \| 扩展：链表有环，如何判断相交

   题目描述：上面的问题都是针对链表无环的，那么如果现在，链表是有环的呢?上面的方法还同样有效么?

9. Find the merged point of two merged linked list \| 扩展：两链表相交的第一个公共节点

   题目描述：如果两个无环单链表相交，怎么求出他们相交的第一个节点呢？


### References

* [Wikipedia: Linked List][3]
* [面试精选：链表问题集锦][2]



[1]: https://raw.githubusercontent.com/fluency03/fluency03.github.io/master/assets/images/2to1.jpg
[2]: http://wuchong.me/blog/2014/03/25/interview-link-questions/
[3]: https://en.wikipedia.org/wiki/Linked_list
[4]: https://upload.wikimedia.org/wikipedia/commons/thumb/6/6d/Singly-linked-list.svg/408px-Singly-linked-list.svg.png
[5]: https://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/Doubly-linked-list.svg/610px-Doubly-linked-list.svg.png
[6]: https://upload.wikimedia.org/wikipedia/commons/thumb/d/df/Circularly-linked-list.svg/350px-Circularly-linked-list.svg.png
