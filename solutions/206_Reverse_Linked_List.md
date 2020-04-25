# 206. 反转链表（简单）

## 题目链接

https://leetcode-cn.com/problems/reverse-linked-list/

## 题目描述

反转一个单链表。

示例：

> 输入: 1->2->3->4->5->NULL
> 输出: 5->4->3->2->1->NULL

**进阶:**
你可以迭代或递归地反转链表。你能否用两种方法解决这道题？

> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/intersection-of-two-linked-lists
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解题思路

1. 迭代法
   - 设置三个指针，current、prev、next分别表示当前节点，上一个节点和下一个节点。
   - 然后遍历单链表进行反转操作。
2. 递归法

## 代码实现

**Golang（迭代法）：**

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func reverseList(head *ListNode) *ListNode {
    current := head
    var prev *ListNode = nil
    
    for current != nil {
        next := current.Next
        current.Next = prev
        prev = current
        current = next
    }
    return prev
}
```

**时间复杂度：**假设链表长度为N，需要遍历整个链表一次，因此时间复杂度为$O(N)$。

**空间复杂度：**$O(1)$。

Golang（递归法）：**

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func reverseList(head *ListNode) *ListNode {
    if head == nil || head.Next == nil {
        return head
    }
    newHead := reverseList(head.Next)
    head.Next.Next = head
    head.Next = nil
    return newHead
}
```

**时间复杂度：**假设链表长度为N，时间复杂度为$O(N)$。

**空间复杂度：**由于使用递归，会使用到栈空间，递归的深度可能达到$O(N)$。