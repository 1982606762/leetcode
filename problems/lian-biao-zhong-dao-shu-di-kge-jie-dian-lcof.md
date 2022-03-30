
# 剑指 Offer 22. 链表中倒数第k个节点 LCOF - 链表中倒数第k个节点

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Linked List-链表-blue.svg">   <img src="https://img.shields.io/badge/Two Pointers-双指针-blue.svg">  


## Description - 题目描述

### EN:
<p>English description is not available for the problem. Please switch to Chinese.</p>

### ZH-CN:
<p>输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。</p>

<p>例如，一个链表有 <code>6</code> 个节点，从头节点开始，它们的值依次是 <code>1、2、3、4、5、6</code>。这个链表的倒数第 <code>3</code> 个节点是值为 <code>4</code> 的节点。</p>

<p> </p>

<p><strong>示例：</strong></p>

<pre>
给定一个链表: <strong>1->2->3->4->5</strong>, 和 <em>k </em><strong>= 2</strong>.

返回链表 4<strong>->5</strong>.</pre>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/description/)  -  [LeetCode-CN](https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| javascript  | 68 ms | 39.1 MB | 2021/07/26 9:50 |

```javascript

/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} k
 * @return {ListNode}
 */
var getKthFromEnd = function(head, k) {
    let p1 = head,p2 = head;
    for(let i = 1;i<k;i++)
    {
        p2=p2.next;
    }while(p2)
    {
        if(!p2.next){
            return p1;
        }
        p1 = p1.next;
        p2 = p2.next;
    }
};

```
## My Notes - 我的笔记


No notes

