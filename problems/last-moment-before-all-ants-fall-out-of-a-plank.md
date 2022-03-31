
# 1503. Last Moment Before All Ants Fall Out of a Plank - 所有蚂蚁掉下来前的最后一刻

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Brainteaser-脑筋急转弯-blue.svg">   <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Simulation-模拟-blue.svg">  


## Description - 题目描述

### EN:
<p>We have a wooden plank of the length <code>n</code> <strong>units</strong>. Some ants are walking on the plank, each ant moves with a speed of <strong>1 unit per second</strong>. Some of the ants move to the <strong>left</strong>, the other move to the <strong>right</strong>.</p>

<p>When two ants moving in two <strong>different</strong> directions meet at some point, they change their directions and continue moving again. Assume changing directions does not take any additional time.</p>

<p>When an ant reaches <strong>one end</strong> of the plank at a time <code>t</code>, it falls out of the plank immediately.</p>

<p>Given an integer <code>n</code> and two integer arrays <code>left</code> and <code>right</code>, the positions of the ants moving to the left and the right, return <em>the moment when the last ant(s) fall out of the plank</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/06/17/ants.jpg" style="width: 450px; height: 610px;" />
<pre>
<strong>Input:</strong> n = 4, left = [4,3], right = [0,1]
<strong>Output:</strong> 4
<strong>Explanation:</strong> In the image above:
-The ant at index 0 is named A and going to the right.
-The ant at index 1 is named B and going to the right.
-The ant at index 3 is named C and going to the left.
-The ant at index 4 is named D and going to the left.
The last moment when an ant was on the plank is t = 4 seconds. After that, it falls immediately out of the plank. (i.e., We can say that at t = 4.0000000001, there are no ants on the plank).
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/06/17/ants2.jpg" style="width: 639px; height: 101px;" />
<pre>
<strong>Input:</strong> n = 7, left = [], right = [0,1,2,3,4,5,6,7]
<strong>Output:</strong> 7
<strong>Explanation:</strong> All ants are going to the right, the ant at index 0 needs 7 seconds to fall.
</pre>

<p><strong>Example 3:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/06/17/ants3.jpg" style="width: 639px; height: 100px;" />
<pre>
<strong>Input:</strong> n = 7, left = [0,1,2,3,4,5,6,7], right = []
<strong>Output:</strong> 7
<strong>Explanation:</strong> All ants are going to the left, the ant at index 7 needs 7 seconds to fall.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= left.length &lt;= n + 1</code></li>
	<li><code>0 &lt;= left[i] &lt;= n</code></li>
	<li><code>0 &lt;= right.length &lt;= n + 1</code></li>
	<li><code>0 &lt;= right[i] &lt;= n</code></li>
	<li><code>1 &lt;= left.length + right.length &lt;= n + 1</code></li>
	<li>All values of <code>left</code> and <code>right</code> are unique, and each value can appear <strong>only in one</strong> of the two arrays.</li>
</ul>


### ZH-CN:
<p>有一块木板，长度为 <code>n</code> 个 <strong>单位</strong> 。一些蚂蚁在木板上移动，每只蚂蚁都以 <strong>每秒一个单位</strong> 的速度移动。其中，一部分蚂蚁向 <strong>左</strong> 移动，其他蚂蚁向 <strong>右</strong> 移动。</p>

<p>当两只向 <strong>不同</strong> 方向移动的蚂蚁在某个点相遇时，它们会同时改变移动方向并继续移动。假设更改方向不会花费任何额外时间。</p>

<p>而当蚂蚁在某一时刻 <code>t</code> 到达木板的一端时，它立即从木板上掉下来。</p>

<p>给你一个整数 <code>n</code> 和两个整数数组 <code>left</code> 以及 <code>right</code> 。两个数组分别标识向左或者向右移动的蚂蚁在 <code>t = 0</code> 时的位置。请你返回最后一只蚂蚁从木板上掉下来的时刻。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p>&nbsp;</p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2020/06/17/ants.jpg" style="height: 610px; width: 450px;" /></p>

<pre>
<strong>输入：</strong>n = 4, left = [4,3], right = [0,1]
<strong>输出：</strong>4
<strong>解释：</strong>如上图所示：
-下标 0 处的蚂蚁命名为 A 并向右移动。
-下标 1 处的蚂蚁命名为 B 并向右移动。
-下标 3 处的蚂蚁命名为 C 并向左移动。
-下标 4 处的蚂蚁命名为 D 并向左移动。
请注意，蚂蚁在木板上的最后时刻是 t = 4 秒，之后蚂蚁立即从木板上掉下来。（也就是说在 t = 4.0000000001 时，木板上没有蚂蚁）。</pre>

<p><strong>示例 2：</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2020/06/17/ants2.jpg" style="height: 101px; width: 639px;" /></p>

<pre>
<strong>输入：</strong>n = 7, left = [], right = [0,1,2,3,4,5,6,7]
<strong>输出：</strong>7
<strong>解释：</strong>所有蚂蚁都向右移动，下标为 0 的蚂蚁需要 7 秒才能从木板上掉落。
</pre>

<p><strong>示例 3：</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2020/06/17/ants3.jpg" style="height: 100px; width: 639px;" /></p>

<pre>
<strong>输入：</strong>n = 7, left = [0,1,2,3,4,5,6,7], right = []
<strong>输出：</strong>7
<strong>解释：</strong>所有蚂蚁都向左移动，下标为 7 的蚂蚁需要 7 秒才能从木板上掉落。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10^4</code></li>
	<li><code>0 &lt;= left.length &lt;= n + 1</code></li>
	<li><code>0 &lt;= left[i] &lt;= n</code></li>
	<li><code>0 &lt;= right.length &lt;= n + 1</code></li>
	<li><code>0 &lt;= right[i] &lt;= n</code></li>
	<li><code>1 &lt;= left.length + right.length &lt;= n + 1</code></li>
	<li><code>left</code> 和 <code>right</code> 中的所有值都是唯一的，并且每个值 <strong>只能出现在二者之一</strong> 中。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/last-moment-before-all-ants-fall-out-of-a-plank/description/)  -  [LeetCode-CN](https://leetcode-cn.com/problems/last-moment-before-all-ants-fall-out-of-a-plank/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
|   |  |  | 1970/01/01 8:00 |

```



```
## My Notes - 我的笔记


No notes

