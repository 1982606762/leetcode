
# 1380. Lucky Numbers in a Matrix - 矩阵中的幸运数

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Matrix-矩阵-blue.svg">  


## Description - 题目描述

### EN:
<p>Given an <code>m x n</code> matrix of <strong>distinct </strong>numbers, return <em>all <strong>lucky numbers</strong> in the matrix in <strong>any </strong>order</em>.</p>

<p>A <strong>lucky number</strong> is an element of the matrix such that it is the minimum element in its row and maximum in its column.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> matrix = [[3,7,8],[9,11,13],[15,16,17]]
<strong>Output:</strong> [15]
<strong>Explanation:</strong> 15 is the only lucky number since it is the minimum in its row and the maximum in its column.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> matrix = [[1,10,4,2],[9,3,8,7],[15,16,17,12]]
<strong>Output:</strong> [12]
<strong>Explanation:</strong> 12 is the only lucky number since it is the minimum in its row and the maximum in its column.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> matrix = [[7,8],[1,2]]
<strong>Output:</strong> [7]
<strong>Explanation:</strong> 7 is the only lucky number since it is the minimum in its row and the maximum in its column.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == mat.length</code></li>
	<li><code>n == mat[i].length</code></li>
	<li><code>1 &lt;= n, m &lt;= 50</code></li>
	<li><code>1 &lt;= matrix[i][j] &lt;= 10<sup>5</sup></code>.</li>
	<li>All elements in the matrix are distinct.</li>
</ul>


### ZH-CN:
<p>给你一个 <code>m * n</code> 的矩阵，矩阵中的数字 <strong>各不相同</strong> 。请你按 <strong>任意</strong> 顺序返回矩阵中的所有幸运数。</p>

<p><strong>幸运数</strong> 是指矩阵中满足同时下列两个条件的元素：</p>

<ul>
	<li>在同一行的所有元素中最小</li>
	<li>在同一列的所有元素中最大</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>matrix = [[3,7,8],[9,11,13],[15,16,17]]
<strong>输出：</strong>[15]
<strong>解释：</strong>15 是唯一的幸运数，因为它是其所在行中的最小值，也是所在列中的最大值。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>matrix = [[1,10,4,2],[9,3,8,7],[15,16,17,12]]
<strong>输出：</strong>[12]
<strong>解释：</strong>12 是唯一的幸运数，因为它是其所在行中的最小值，也是所在列中的最大值。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>matrix = [[7,8],[1,2]]
<strong>输出：</strong>[7]
<strong>解释：</strong>7是唯一的幸运数字，因为它是行中的最小值，列中的最大值。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>m == mat.length</code></li>
	<li><code>n == mat[i].length</code></li>
	<li><code>1 &lt;= n, m &lt;= 50</code></li>
	<li><code>1 &lt;=&nbsp;matrix[i][j]&nbsp;&lt;= 10^5</code></li>
	<li>矩阵中的所有元素都是不同的</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/lucky-numbers-in-a-matrix/description/)  -  [LeetCode-CN](https://leetcode-cn.com/problems/lucky-numbers-in-a-matrix/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 44 ms | 10.1 MB | 2020/03/15 13:48 |

```cpp

class Solution {
public:
    vector<int> luckyNumbers (vector<vector<int>>& matrix) {
        vector<int >  Myres;//存储结果
        int m=matrix.size();
        if(m==0){
            return Myres;
        }
        int n=matrix[0].size();
        vector<bool > block(n,0);
        vector<vector<bool >> tmp;//一个与matrix同大小的数组
        for(int i=0;i<m;i++){
            tmp.push_back(block);
        }
        for(int i=0;i<m;i++){     //记录每行最小数值的位置，找到后把tmp上对应位置标记出来
            int ix=i;
            int jx=0;
            int imin=matrix[i][0];
            for(int j=0;j<n;j++){
                if(imin>=matrix[i][j]){
                    imin=matrix[i][j];
                    ix=i;
                    jx=j;
                }
            }
            tmp[ix][jx]=1;
        }
        for(int i=0;i<n;i++){       //记录每一列中最大的位置，找到后查看是否为行中最小的位置
            int jx=i;
            int ix=0;
            int imax=matrix[0][i];
            for(int j=0;j<m;j++){
                if(imax<=matrix[j][i]){
                    imax=matrix[j][i];
                    ix=j;
                    jx=i;
                }         
            }
            if(tmp[ix][jx]==1){     //如果是，那么就存储下来
                Myres.push_back(matrix[ix][jx]);
            }
        }
        return Myres;
        
    }
};


```
## My Notes - 我的笔记


No notes

