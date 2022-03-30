
# 1505. Minimum Possible Integer After at Most K Adjacent Swaps On Digits - 最多 K 次交换相邻数位后得到的最小整数

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Greedy-贪心-blue.svg">   <img src="https://img.shields.io/badge/Binary Indexed Tree-树状数组-blue.svg">   <img src="https://img.shields.io/badge/Segment Tree-线段树-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given a string <code>num</code> representing <strong>the digits</strong> of a very large integer and an integer <code>k</code>. You are allowed to swap any two adjacent digits of the integer <strong>at most</strong> <code>k</code> times.</p>

<p>Return <em>the minimum integer you can obtain also as a string</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/06/17/q4_1.jpg" style="width: 500px; height: 40px;" />
<pre>
<strong>Input:</strong> num = &quot;4321&quot;, k = 4
<strong>Output:</strong> &quot;1342&quot;
<strong>Explanation:</strong> The steps to obtain the minimum integer from 4321 with 4 adjacent swaps are shown.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> num = &quot;100&quot;, k = 1
<strong>Output:</strong> &quot;010&quot;
<strong>Explanation:</strong> It&#39;s ok for the output to have leading zeros, but the input is guaranteed not to have any leading zeros.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> num = &quot;36789&quot;, k = 1000
<strong>Output:</strong> &quot;36789&quot;
<strong>Explanation:</strong> We can keep the number without any swaps.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>num</code> consists of only <strong>digits</strong> and does not contain <strong>leading zeros</strong>.</li>
	<li><code>1 &lt;= k &lt;= 10<sup>4</sup></code></li>
</ul>


### ZH-CN:
<p>给你一个字符串&nbsp;<code>num</code> 和一个整数&nbsp;<code>k</code> 。其中，<code>num</code> 表示一个很大的整数，字符串中的每个字符依次对应整数上的各个 <strong>数位</strong> 。</p>

<p>你可以交换这个整数相邻数位的数字 <strong>最多</strong>&nbsp;<code>k</code>&nbsp;次。</p>

<p>请你返回你能得到的最小整数，并以字符串形式返回。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2020/06/17/q4_1.jpg" style="height:40px; width:500px" /></p>

<pre>
<strong>输入：</strong>num = &quot;4321&quot;, k = 4
<strong>输出：</strong>&quot;1342&quot;
<strong>解释：</strong>4321 通过 4 次交换相邻数位得到最小整数的步骤如上图所示。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>num = &quot;100&quot;, k = 1
<strong>输出：</strong>&quot;010&quot;
<strong>解释：</strong>输出可以包含前导 0 ，但输入保证不会有前导 0 。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>num = &quot;36789&quot;, k = 1000
<strong>输出：</strong>&quot;36789&quot;
<strong>解释：</strong>不需要做任何交换。
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>num = &quot;22&quot;, k = 22
<strong>输出：</strong>&quot;22&quot;
</pre>

<p><strong>示例 5：</strong></p>

<pre>
<strong>输入：</strong>num = &quot;9438957234785635408&quot;, k = 23
<strong>输出：</strong>&quot;0345989723478563548&quot;
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= num.length &lt;= 30000</code></li>
	<li><code>num</code>&nbsp;只包含&nbsp;<strong>数字</strong>&nbsp;且不含有<strong>&nbsp;前导 0&nbsp;</strong>。</li>
	<li><code>1 &lt;= k &lt;= 10^9</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/minimum-possible-integer-after-at-most-k-adjacent-swaps-on-digits/description/)  -  [LeetCode-CN](https://leetcode-cn.com/problems/minimum-possible-integer-after-at-most-k-adjacent-swaps-on-digits/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 276 ms | 11.4 MB | 2020/07/08 21:38 |

```cpp

class Solution {
    //预处理字符位置的优先队列
    priority_queue<int, vector<int>, greater<int>> pq[10];
    
    int st[30001*4]; //线段树所需的数组
    //更新线段树的代码
    void update(int root, int L, int R, int goal) {
        st[root] += 1;
        if(L == R) {
            return ;
        }
        int mid = (L+R)>>1;
        if(goal <= mid) {
            update(root<<1, L, mid, goal);
        } else {
            update(root<<1|1, mid+1, R, goal);
        } 
    }
    //线段树查询代码
    int query(int root, int L, int R, int goal) {
        if(R == goal) {
            return st[root];
        }
        int mid = (L+R)>>1;
        if(mid < goal) {
            return st[root<<1] + query(root<<1|1, mid+1, R, goal);
        }
        return query(root<<1, L, mid, goal);
    }
public:
    string minInteger(string num, int k) {
        memset(st, 0, sizeof(st));
        //处理字符位置
        for(int i = 0; i < num.size(); i++) {
            pq[num[i]-'0'].push(i);
        }
        string anw;
        while(anw.size() < num.size()) {
            for(int i = 0; i < 10; i++) { //枚举字符
                if(pq[i].size() <= 0) { 
                    continue;
                }
                //pq[i].top()为当前字符最靠近目标位置的下标
                int cost = pq[i].top() - query(1, 1, 30000, pq[i].top()+1);
                if(cost <= k) {
                    k -= cost;
                    anw += char(i+'0');
                    update(1, 1, 30000, pq[i].top()+1);
                    pq[i].pop();
                    break;
                }
            }
        }
        return anw;
    }
};


```
## My Notes - 我的笔记


No notes

