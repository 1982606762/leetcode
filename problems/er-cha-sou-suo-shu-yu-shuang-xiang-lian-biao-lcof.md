
# 剑指 Offer 36. 二叉搜索树与双向链表  LCOF - 二叉搜索树与双向链表

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Stack-栈-blue.svg">   <img src="https://img.shields.io/badge/Tree-树-blue.svg">   <img src="https://img.shields.io/badge/Depth-First Search-深度优先搜索-blue.svg">   <img src="https://img.shields.io/badge/Binary Search Tree-二叉搜索树-blue.svg">   <img src="https://img.shields.io/badge/Linked List-链表-blue.svg">   <img src="https://img.shields.io/badge/Binary Tree-二叉树-blue.svg">   <img src="https://img.shields.io/badge/Doubly-Linked List-双向链表-blue.svg">  


## Description - 题目描述

### EN:
English description is not available for the problem. Please switch to Chinese.

### ZH-CN:
<p>输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的循环双向链表。要求不能创建任何新的节点，只能调整树中节点指针的指向。</p>

<p>&nbsp;</p>

<p>为了让您更好地理解问题，以下面的二叉搜索树为例：</p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode.com/uploads/2018/10/12/bstdlloriginalbst.png"></p>

<p>&nbsp;</p>

<p>我们希望将这个二叉搜索树转化为双向循环链表。链表中的每个节点都有一个前驱和后继指针。对于双向循环链表，第一个节点的前驱是最后一个节点，最后一个节点的后继是第一个节点。</p>

<p>下图展示了上面的二叉搜索树转化成的链表。&ldquo;head&rdquo; 表示指向链表中有最小元素的节点。</p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode.com/uploads/2018/10/12/bstdllreturndll.png"></p>

<p>&nbsp;</p>

<p>特别地，我们希望可以就地完成转换操作。当转化完成以后，树中节点的左指针需要指向前驱，树中节点的右指针需要指向后继。还需要返回链表中的第一个节点的指针。</p>

<p>&nbsp;</p>

<p><strong>注意：</strong>本题与主站 426 题相同：<a href="https://leetcode-cn.com/problems/convert-binary-search-tree-to-sorted-doubly-linked-list/">https://leetcode-cn.com/problems/convert-binary-search-tree-to-sorted-doubly-linked-list/</a></p>

<p><strong>注意：</strong>此题对比原题有改动。</p>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/er-cha-sou-suo-shu-yu-shuang-xiang-lian-biao-lcof/description/)  -  [LeetCode-CN](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-yu-shuang-xiang-lian-biao-lcof/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| javascript  | 76 ms | 39.1 MB | 2021/07/23 12:05 |

```javascript

/**
 * // Definition for a Node.
 * function Node(val,left,right) {
 *    this.val = val;
 *    this.left = left;
 *    this.right = right;
 * };
 */
/**
 * @param {Node} root
 * @return {Node}
 */
var treeToDoublyList = function(root) {

    //特殊情况的考虑
    if(!root) return null;

    //1.进行中序遍历,存入每个节点的指针
    let nodeSet=[];
    const inOrder=node=>{
        if(!node){
            return;
        }
        inOrder(node.left);
        let p=node;
        nodeSet.push(p);
        inOrder(node.right);
    };
    inOrder(root);

    //2.连接成循环双向链表
    if(nodeSet.length===1){
        nodeSet[0].left=nodeSet[0];
        nodeSet[0].right=nodeSet[0];
    }else{
        for(let i=1;i<nodeSet.length-1;i++){
            //首尾结点待会单独考虑
            nodeSet[i].left=nodeSet[i-1];
            nodeSet[i].right=nodeSet[i+1];
        }
        nodeSet[0].left=nodeSet[nodeSet.length-1];
        nodeSet[0].right=nodeSet[1];
        nodeSet[nodeSet.length-1].right=nodeSet[0];
        nodeSet[nodeSet.length-1].left=nodeSet[nodeSet.length-2];
    }
    return nodeSet[0];

};


```
## My Notes - 我的笔记


No notes

