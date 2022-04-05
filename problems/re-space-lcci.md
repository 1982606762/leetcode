
# 面试题 17.13. Re-Space LCCI - 恢复空格

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Trie-字典树-blue.svg">   <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">   <img src="https://img.shields.io/badge/Hash Function-哈希函数-blue.svg">   <img src="https://img.shields.io/badge/Rolling Hash-滚动哈希-blue.svg">  


## Description - 题目描述

### EN:
<p>Oh, no! You have accidentally removed all spaces, punctuation, and capitalization in a lengthy document. A sentence like &quot;I reset the computer. It still didn&#39;t boot!&quot; became &quot;iresetthecomputeritstilldidntboot&#39;&#39;. You&#39;ll deal with the punctuation and capi&shy;talization later; right now you need to re-insert the spaces. Most of the words are in a dictionary but a few are not. Given a dictionary (a list of strings) and the document (a string), design an algorithm to unconcatenate the document in a way that minimizes the number of unrecognized characters. Return the number of unrecognized characters.</p>

<p><strong>Note: </strong>This&nbsp;problem is slightly different from the original one in the book.</p>

<p>&nbsp;</p>

<p><strong>Example: </strong></p>

<pre>
<strong>Input: </strong>
dictionary = [&quot;looked&quot;,&quot;just&quot;,&quot;like&quot;,&quot;her&quot;,&quot;brother&quot;]
sentence = &quot;jesslookedjustliketimherbrother&quot;
<strong>Output: </strong> 7
<strong>Explanation: </strong> After unconcatenating, we got &quot;<strong>jess</strong> looked just like <strong>tim</strong> her brother&quot;, which containing 7 unrecognized characters.
</pre>

<p><strong>Note: </strong></p>

<ul>
	<li><code>0 &lt;= len(sentence) &lt;= 1000</code></li>
	<li><code><font face="sans-serif, Arial, Verdana, Trebuchet MS">The total number of characters in&nbsp;</font>dictionary</code>&nbsp;is less than or equal to 150000.</li>
	<li>There are only lowercase letters in&nbsp;<code>dictionary</code>&nbsp;and&nbsp;<code>sentence</code>.</li>
</ul>


### ZH-CN:
<p>哦，不！你不小心把一个长篇文章中的空格、标点都删掉了，并且大写也弄成了小写。像句子<code>&quot;I reset the computer. It still didn&rsquo;t boot!&quot;</code>已经变成了<code>&quot;iresetthecomputeritstilldidntboot&quot;</code>。在处理标点符号和大小写之前，你得先把它断成词语。当然了，你有一本厚厚的词典<code>dictionary</code>，不过，有些词没在词典里。假设文章用<code>sentence</code>表示，设计一个算法，把文章断开，要求未识别的字符最少，返回未识别的字符数。</p>

<p><strong>注意：</strong>本题相对原题稍作改动，只需返回未识别的字符数</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>
dictionary = [&quot;looked&quot;,&quot;just&quot;,&quot;like&quot;,&quot;her&quot;,&quot;brother&quot;]
sentence = &quot;jesslookedjustliketimherbrother&quot;
<strong>输出：</strong> 7
<strong>解释：</strong> 断句后为&quot;<strong>jess</strong> looked just like <strong>tim</strong> her brother&quot;，共7个未识别字符。
</pre>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 &lt;= len(sentence) &lt;= 1000</code></li>
	<li><code>dictionary</code>中总字符数不超过 150000。</li>
	<li>你可以认为<code>dictionary</code>和<code>sentence</code>中只包含小写字母。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/re-space-lcci/description/)  -  [LeetCode-CN](https://leetcode-cn.com/problems/re-space-lcci/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 744 ms | 195.6 MB | 2020/07/09 17:09 |

```cpp

class Solution {
public:
    /*void dfs(unordered_set<string>& maps, string sentence, int cnt, int& ans)
    {
        if(sentence.size() == 0)
        {
            ans = min(ans,cnt);
            return ;
        }
        for(int i = 1; i<=sentence.size(); i++)
        {
            string temp = sentence.substr(0,i);
            if(maps.find(temp) != maps.end())
                dfs(maps,sentence.substr(i,sentence.size()-i),cnt,ans);
            else
                dfs(maps,sentence.substr(i,sentence.size()-i),cnt+1,ans);
        }
        return ;
    }*/
    int respace(vector<string>& dictionary, string sentence) {
        //int ans = 1e9;
        //unordered_set<string> maps;
        //for(auto t : dictionary)
            //maps.insert(t);
        // dfs(maps,sentence,0,ans);
        
        int sen_len = sentence.size();
        vector<int> dp(sen_len+1);      //dp[i]表示sentence前i个字符里面未识别的字符数

        dp[0] = 0;
        for(int i = 1; i<=sen_len; i++)
        {
            dp[i] = dp[i-1]+1;
            for(int j=0; j<dictionary.size(); j++)
            {
                int len = dictionary[j].size();
                if(len <= i)
                {
                    if(sentence.substr(i-len,len)==dictionary[j])
                        dp[i]=min(dp[i],dp[i-len]);
                }
            }

        }

        return dp[sen_len];
    }
};


```
## My Notes - 我的笔记


No notes

