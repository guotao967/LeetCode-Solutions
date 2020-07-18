# 144. Binary Tree Preorder Traversal

## 题目链接

https://leetcode-cn.com/problems/binary-tree-preorder-traversal/

## 代码实现
- 递归法
```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
var res []int
func preorderTraversal(root *TreeNode) []int {
    res = make([]int, 0)
    dfs(root)
    return res
}

func dfs(root *TreeNode) {
    if root == nil {
        return
    }
    res = append(res, root.Val)
    dfs(root.Left)
    dfs(root.Right)
}
```
- 迭代法
```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func preorderTraversal(root *TreeNode) []int {
    res := make([]int, 0)
    stack := make([]*TreeNode, 0)

    p := root
    for p != nil || len(stack) > 0 {
        for p != nil {
            res = append(res, p.Val)
            stack = append(stack, p.Right)
            p = p.Left
        }
        p = stack[len(stack)-1]
        stack = stack[:len(stack)-1]
    }
    return res
}
```