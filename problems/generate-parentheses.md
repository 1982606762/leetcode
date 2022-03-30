
# 22. Generate Parentheses - 括号生成

## Tags - 题目标签

 <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">   <img src="https://img.shields.io/badge/Backtracking-回溯-blue.svg">  


## Description - 题目描述

### EN:
<p>Given <code>n</code> pairs of parentheses, write a function to <em>generate all combinations of well-formed parentheses</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> n = 3
<strong>Output:</strong> ["((()))","(()())","(())()","()(())","()()()"]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> n = 1
<strong>Output:</strong> ["()"]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 8</code></li>
</ul>


### ZH-CN:
<p>数字 <code>n</code>&nbsp;代表生成括号的对数，请你设计一个函数，用于能够生成所有可能的并且 <strong>有效的 </strong>括号组合。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 3
<strong>输出：</strong>["((()))","(()())","(())()","()(())","()()()"]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 1
<strong>输出：</strong>["()"]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 8</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/generate-parentheses/description/)  -  [LeetCode-CN](https://leetcode-cn.com/problems/generate-parentheses/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 13.4 MB | 2022/02/19 9:34 |

```cpp

class Solution {
public:
    vector<string> resvec;

    vector<string> generateParenthesis(int n) {
    string s = "";
    gen(s,n,n);
    return resvec;
    }
    void gen(string s,int left,int right){
    if(left == 0 && right == 0){
        resvec.push_back(s);
        return;
    }
    if(left == right){
        gen(s+"(",left-1,right);
    }else{
        if(left<right){
            if(left>0){
                gen(s+"(",left-1,right);
            }
            gen(s+")",left,right-1);
        }
    }
}
};

```
## My Notes - 我的笔记


No notes

