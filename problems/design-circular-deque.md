
# 641. Design Circular Deque - 设计循环双端队列

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Design-设计-blue.svg">   <img src="https://img.shields.io/badge/Queue-队列-blue.svg">   <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Linked List-链表-blue.svg">  


## Description - 题目描述

### EN:
<p>Design your implementation of the circular double-ended queue (deque).</p>

<p>Implement the <code>MyCircularDeque</code> class:</p>

<ul>
	<li><code>MyCircularDeque(int k)</code> Initializes the deque with a maximum size of <code>k</code>.</li>
	<li><code>boolean insertFront()</code> Adds an item at the front of Deque. Returns <code>true</code> if the operation is successful, or <code>false</code> otherwise.</li>
	<li><code>boolean insertLast()</code> Adds an item at the rear of Deque. Returns <code>true</code> if the operation is successful, or <code>false</code> otherwise.</li>
	<li><code>boolean deleteFront()</code> Deletes an item from the front of Deque. Returns <code>true</code> if the operation is successful, or <code>false</code> otherwise.</li>
	<li><code>boolean deleteLast()</code> Deletes an item from the rear of Deque. Returns <code>true</code> if the operation is successful, or <code>false</code> otherwise.</li>
	<li><code>int getFront()</code> Returns the front item from the Deque. Returns <code>-1</code> if the deque is empty.</li>
	<li><code>int getRear()</code> Returns the last item from Deque. Returns <code>-1</code> if the deque is empty.</li>
	<li><code>boolean isEmpty()</code> Returns <code>true</code> if the deque is empty, or <code>false</code> otherwise.</li>
	<li><code>boolean isFull()</code> Returns <code>true</code> if the deque is full, or <code>false</code> otherwise.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input</strong>
[&quot;MyCircularDeque&quot;, &quot;insertLast&quot;, &quot;insertLast&quot;, &quot;insertFront&quot;, &quot;insertFront&quot;, &quot;getRear&quot;, &quot;isFull&quot;, &quot;deleteLast&quot;, &quot;insertFront&quot;, &quot;getFront&quot;]
[[3], [1], [2], [3], [4], [], [], [], [4], []]
<strong>Output</strong>
[null, true, true, true, false, 2, true, true, true, 4]

<strong>Explanation</strong>
MyCircularDeque myCircularDeque = new MyCircularDeque(3);
myCircularDeque.insertLast(1);  // return True
myCircularDeque.insertLast(2);  // return True
myCircularDeque.insertFront(3); // return True
myCircularDeque.insertFront(4); // return False, the queue is full.
myCircularDeque.getRear();      // return 2
myCircularDeque.isFull();       // return True
myCircularDeque.deleteLast();   // return True
myCircularDeque.insertFront(4); // return True
myCircularDeque.getFront();     // return 4
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= 1000</code></li>
	<li><code>0 &lt;= value &lt;= 1000</code></li>
	<li>At most <code>2000</code> calls will be made to <code>insertFront</code>, <code>insertLast</code>, <code>deleteFront</code>, <code>deleteLast</code>, <code>getFront</code>, <code>getRear</code>, <code>isEmpty</code>, <code>isFull</code>.</li>
</ul>


### ZH-CN:
<p>设计实现双端队列。</p>

<p>实现 <code>MyCircularDeque</code> 类:</p>

<ul>
	<li><code>MyCircularDeque(int k)</code>&nbsp;：构造函数,双端队列最大为 <code>k</code> 。</li>
	<li><code>boolean insertFront()</code>：将一个元素添加到双端队列头部。 如果操作成功返回 <code>true</code>&nbsp;，否则返回 <code>false</code> 。</li>
	<li><code>boolean insertLast()</code>&nbsp;：将一个元素添加到双端队列尾部。如果操作成功返回 <code>true</code>&nbsp;，否则返回 <code>false</code> 。</li>
	<li><code>boolean deleteFront()</code>&nbsp;：从双端队列头部删除一个元素。 如果操作成功返回 <code>true</code>&nbsp;，否则返回 <code>false</code> 。</li>
	<li><code>boolean deleteLast()</code>&nbsp;：从双端队列尾部删除一个元素。如果操作成功返回 <code>true</code>&nbsp;，否则返回 <code>false</code> 。</li>
	<li><code>int getFront()</code>&nbsp;)：从双端队列头部获得一个元素。如果双端队列为空，返回 <code>-1</code>&nbsp;。</li>
	<li><code>int getRear()</code>&nbsp;：获得双端队列的最后一个元素。&nbsp;如果双端队列为空，返回 <code>-1</code> 。</li>
	<li><code>boolean isEmpty()</code>&nbsp;：若双端队列为空，则返回&nbsp;<code>true</code>&nbsp;，否则返回 <code>false</code> &nbsp;。</li>
	<li><code>boolean isFull()</code>&nbsp;：若双端队列满了，则返回&nbsp;<code>true</code>&nbsp;，否则返回 <code>false</code> 。</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入</strong>
["MyCircularDeque", "insertLast", "insertLast", "insertFront", "insertFront", "getRear", "isFull", "deleteLast", "insertFront", "getFront"]
[[3], [1], [2], [3], [4], [], [], [], [4], []]
<strong>输出</strong>
[null, true, true, true, false, 2, true, true, true, 4]

<strong>解释</strong>
MyCircularDeque circularDeque = new MycircularDeque(3); // 设置容量大小为3
circularDeque.insertLast(1);			        // 返回 true
circularDeque.insertLast(2);			        // 返回 true
circularDeque.insertFront(3);			        // 返回 true
circularDeque.insertFront(4);			        // 已经满了，返回 false
circularDeque.getRear();  				// 返回 2
circularDeque.isFull();				        // 返回 true
circularDeque.deleteLast();			        // 返回 true
circularDeque.insertFront(4);			        // 返回 true
circularDeque.getFront();				// 返回 4
&nbsp;</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= 1000</code></li>
	<li><code>0 &lt;= value &lt;= 1000</code></li>
	<li><code>insertFront</code>,&nbsp;<code>insertLast</code>,&nbsp;<code>deleteFront</code>,&nbsp;<code>deleteLast</code>,&nbsp;<code>getFront</code>,&nbsp;<code>getRear</code>,&nbsp;<code>isEmpty</code>,&nbsp;<code>isFull</code>&nbsp; 调用次数不大于&nbsp;<code>2000</code>&nbsp;次</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/design-circular-deque/description/)  -  [LeetCode-CN](https://leetcode-cn.com/problems/design-circular-deque/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
|   |  |  | 1970/01/01 8:00 |

```



```
## My Notes - 我的笔记


No notes

