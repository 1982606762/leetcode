
# 面试题 16.11. Diving Board LCCI - 跳水板

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">  


## Description - 题目描述

### EN:
<p>You are building a diving board by placing a bunch of planks of wood end-to-end. There are two types of planks, one of length <code>shorter</code> and one of length <code>longer</code>. You must use exactly <code>K</code> planks of wood. Write a method to generate all possible lengths for the diving board.</p>

<p>return all lengths in non-decreasing order.</p>

<p><strong>Example: </strong></p>

<pre>
<strong>Input: </strong>
shorter = 1
longer = 2
k = 3
<strong>Output: </strong> {3,4,5,6}
</pre>

<p><strong>Note: </strong></p>

<ul>
	<li>0 &lt; shorter &lt;= longer</li>
	<li>0 &lt;= k &lt;= 100000</li>
</ul>


### ZH-CN:
<p>你正在使用一堆木板建造跳水板。有两种类型的木板，其中长度较短的木板长度为<code>shorter</code>，长度较长的木板长度为<code>longer</code>。你必须正好使用<code>k</code>块木板。编写一个方法，生成跳水板所有可能的长度。</p>

<p>返回的长度需要从小到大排列。</p>

<p><strong>示例 1</strong></p>

<pre><code><strong>输入：</strong>
shorter = 1
longer = 2
k = 3
<strong>输出：</strong> [3,4,5,6]
<strong>解释：</strong>
可以使用 3 次 shorter，得到结果 3；使用 2 次 shorter 和 1 次 longer，得到结果 4 。以此类推，得到最终结果。</code></pre>

<p><strong>提示：</strong></p>

<ul>
	<li>0 &lt; shorter &lt;= longer</li>
	<li>0 &lt;= k &lt;= 100000</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/diving-board-lcci/description/)  -  [LeetCode-CN](https://leetcode-cn.com/problems/diving-board-lcci/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 20 ms | 19.8 MB | 2020/07/08 12:21 |

```cpp

class Solution {
public:
    vector<int> divingBoard(int shorter, int longer, int k) {
        vector<int> ans;
        if(k==0)
        {
            return ans;
        }
        else if(shorter==longer)
        {
            ans.push_back(shorter*k);
            return ans;
        }else{
            int temp = shorter*k;
            ans.push_back(temp);
        for(int i=k;i>0;i--)
        {
            temp=temp-shorter+longer;
            ans.push_back(temp);
        }
        return ans;
        }
    }
};

```
## My Notes - 我的笔记


No notes

