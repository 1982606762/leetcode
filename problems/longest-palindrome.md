
# 409. Longest Palindrome - 最长回文串

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Greedy-贪心-blue.svg">   <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>Given a string <code>s</code> which consists of lowercase or uppercase letters, return <em>the length of the <strong>longest palindrome</strong></em>&nbsp;that can be built with those letters.</p>

<p>Letters are <strong>case sensitive</strong>, for example,&nbsp;<code>&quot;Aa&quot;</code> is not considered a palindrome here.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abccccdd&quot;
<strong>Output:</strong> 7
<strong>Explanation:</strong>
One longest palindrome that can be built is &quot;dccaccd&quot;, whose length is 7.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;a&quot;
<strong>Output:</strong> 1
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;bb&quot;
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 2000</code></li>
	<li><code>s</code> consists of lowercase <strong>and/or</strong> uppercase English&nbsp;letters only.</li>
</ul>


### ZH-CN:
<p>给定一个包含大写字母和小写字母的字符串<meta charset="UTF-8" />&nbsp;<code>s</code>&nbsp;，返回&nbsp;<em>通过这些字母构造成的 <strong>最长的回文串</strong></em>&nbsp;。</p>

<p>在构造过程中，请注意 <strong>区分大小写</strong> 。比如&nbsp;<code>"Aa"</code>&nbsp;不能当做一个回文字符串。</p>

<p>&nbsp;</p>

<p><strong>示例 1: </strong></p>

<pre>
<strong>输入:</strong>s = "abccccdd"
<strong>输出:</strong>7
<strong>解释:</strong>
我们可以构造的最长的回文串是"dccaccd", 它的长度是 7。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong>s = "a"
<strong>输入:</strong>1
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入:</strong>s = "bb"
<strong>输入:</strong> 2
</pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 2000</code></li>
	<li><code>s</code>&nbsp;只能由小写和/或大写英文字母组成</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/longest-palindrome/description/)  -  [LeetCode-CN](https://leetcode-cn.com/problems/longest-palindrome/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 8 ms | 8.6 MB | 2019/10/09 20:04 |

```cpp

class Solution {
public:
    int longestPalindrome(string s) {
		vector<int> v(52, 0);
 		for (int i = 0; i < s.size(); i++) {
 			if(isupper(s[i])) v[26 + s[i] - 'A']++;
			else v[s[i] - 'a']++;
 		}       
		int ans = 0;
		for (int i = 0; i < 52; i++) {
			if(!(v[i] & 1)) ans += v[i];
			else{
				if(v[i] > 2) ans += v[i] - 1;
			}
		}
		if(ans < s.size()) ans++;
		return ans;
    }
};



```
## My Notes - 我的笔记


No notes

