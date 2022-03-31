
# 面试题 02.07. Intersection of Two Linked Lists LCCI - 链表相交

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/Linked List-链表-blue.svg">   <img src="https://img.shields.io/badge/Two Pointers-双指针-blue.svg">  


## Description - 题目描述

### EN:
<p>Given two (singly) linked lists, determine if the two lists intersect. Return the inter&shy; secting node. Note that the intersection is defined based on reference, not value. That is, if the kth node of the first linked list is the exact same node (by reference) as the jth node of the second linked list, then they are intersecting.</p>

<p><strong>Example 1: </strong></p>

<pre>
<strong>Input: </strong>intersectVal = 8, listA = [4,1,8,4,5], listB = [5,0,1,8,4,5], skipA = 2, skipB = 3
<strong>Output: </strong>Reference of the node with value = 8
<strong>Input Explanation:</strong> The intersected node&#39;s value is 8 (note that this must not be 0 if the two lists intersect). From the head of A, it reads as [4,1,8,4,5]. From the head of B, it reads as [5,0,1,8,4,5]. There are 2 nodes before the intersected node in A; There are 3 nodes before the intersected node in B.</pre>

<p><strong>Example 2: </strong></p>

<pre>
<strong>Input: </strong>intersectVal = 2, listA = [0,9,1,2,4], listB = [3,2,4], skipA = 3, skipB = 1
<strong>Output: </strong>Reference of the node with value = 2
<strong>Input Explanation:</strong>&nbsp;The intersected node&#39;s value is 2 (note that this must not be 0 if the two lists intersect). From the head of A, it reads as [0,9,1,2,4]. From the head of B, it reads as [3,2,4]. There are 3 nodes before the intersected node in A; There are 1 node before the intersected node in B.</pre>

<p><strong>Example 3: </strong></p>

<pre>
<strong>Input: </strong>intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2
<strong>Output: </strong>null
<strong>Input Explanation:</strong> From the head of A, it reads as [2,6,4]. From the head of B, it reads as [1,5]. Since the two lists do not intersect, intersectVal must be 0, while skipA and skipB can be arbitrary values.
<strong>Explanation:</strong> The two lists do not intersect, so return null.</pre>

<p><b>Notes:</b></p>

<ul>
	<li>If the two linked lists have no intersection at all, return&nbsp;<code>null</code>.</li>
	<li>The linked lists must retain their original structure after the function returns.</li>
	<li>You may assume there are no cycles anywhere in the entire linked structure.</li>
	<li>Your code should preferably run in O(n) time and use only O(1) memory.</li>
</ul>


### ZH-CN:
<p>给你两个单链表的头节点 <code>headA</code> 和 <code>headB</code> ，请你找出并返回两个单链表相交的起始节点。如果两个链表没有交点，返回 <code>null</code> 。</p>

<p>图示两个链表在节点 <code>c1</code> 开始相交<strong>：</strong></p>

<p><a href="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/160_statement.png" target="_blank"><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/160_statement.png" style="height: 130px; width: 400px;" /></a></p>

<p>题目数据 <strong>保证</strong> 整个链式结构中不存在环。</p>

<p><strong>注意</strong>，函数返回结果后，链表必须 <strong>保持其原始结构</strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<p><a href="https://assets.leetcode.com/uploads/2018/12/13/160_example_1.png" target="_blank"><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/160_example_1.png" style="height: 130px; width: 400px;" /></a></p>

<pre>
<strong>输入：</strong>intersectVal = 8, listA = [4,1,8,4,5], listB = [5,0,1,8,4,5], skipA = 2, skipB = 3
<strong>输出：</strong>Intersected at '8'
<strong>解释：</strong>相交节点的值为 8 （注意，如果两个链表相交则不能为 0）。
从各自的表头开始算起，链表 A 为 [4,1,8,4,5]，链表 B 为 [5,0,1,8,4,5]。
在 A 中，相交节点前有 2 个节点；在 B 中，相交节点前有 3 个节点。
</pre>

<p><strong>示例 2：</strong></p>

<p><a href="https://assets.leetcode.com/uploads/2018/12/13/160_example_2.png" target="_blank"><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/160_example_2.png" style="height: 136px; width: 350px;" /></a></p>

<pre>
<strong>输入：</strong>intersectVal = 2, listA = [0,9,1,2,4], listB = [3,2,4], skipA = 3, skipB = 1
<strong>输出：</strong>Intersected at '2'
<strong>解释：</strong>相交节点的值为 2 （注意，如果两个链表相交则不能为 0）。
从各自的表头开始算起，链表 A 为 [0,9,1,2,4]，链表 B 为 [3,2,4]。
在 A 中，相交节点前有 3 个节点；在 B 中，相交节点前有 1 个节点。
</pre>

<p><strong>示例 3：</strong></p>

<p><a href="https://assets.leetcode.com/uploads/2018/12/13/160_example_3.png" target="_blank"><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/160_example_3.png" style="height: 126px; width: 200px;" /></a></p>

<pre>
<strong>输入：</strong>intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2
<strong>输出：</strong>null
<strong>解释：</strong>从各自的表头开始算起，链表 A 为 [2,6,4]，链表 B 为 [1,5]。
由于这两个链表不相交，所以 intersectVal 必须为 0，而 skipA 和 skipB 可以是任意值。
这两个链表不相交，因此返回 null 。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>listA</code> 中节点数目为 <code>m</code></li>
	<li><code>listB</code> 中节点数目为 <code>n</code></li>
	<li><code>0 <= m, n <= 3 * 10<sup>4</sup></code></li>
	<li><code>1 <= Node.val <= 10<sup>5</sup></code></li>
	<li><code>0 <= skipA <= m</code></li>
	<li><code>0 <= skipB <= n</code></li>
	<li>如果 <code>listA</code> 和 <code>listB</code> 没有交点，<code>intersectVal</code> 为 <code>0</code></li>
	<li>如果 <code>listA</code> 和 <code>listB</code> 有交点，<code>intersectVal == listA[skipA + 1] == listB[skipB + 1]</code></li>
</ul>

<p> </p>

<p><strong>进阶：</strong>你能否设计一个时间复杂度 <code>O(n)</code> 、仅用 <code>O(1)</code> 内存的解决方案？</p>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/intersection-of-two-linked-lists-lcci/description/)  -  [LeetCode-CN](https://leetcode-cn.com/problems/intersection-of-two-linked-lists-lcci/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 40 ms | 14 MB | 2022/03/31 13:02 |

```cpp

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode *res = NULL;
        ListNode *a = headA , *b = headB;
        int alen = 0,blen = 0;
        while(a){
            alen ++;
            a = a->next;
        }
        while(b){
            blen ++;
            b = b->next;
        }
        a = headA;
        b = headB;
        int dif;
        if(alen > blen){
            dif = alen - blen;
            while (dif --) {
                a = a->next;
            }
        }else{
            dif = blen - alen;
            while(dif --){
                b = b->next;
            }
        }
        while(a && b){
            if(a == b){
               res = a;
               return res;
            }
            a = a->next;
            b = b->next;
        }
        return NULL;
    }
};

```
## My Notes - 我的笔记


No notes

