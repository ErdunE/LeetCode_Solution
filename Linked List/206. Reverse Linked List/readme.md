## 206. Reverse Linked List

#### 中文题目链接[206. 反转链表](https://leetcode-cn.com/problems/reverse-linked-list/)

#### 英文题目链接[206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

- Given the `head` of a singly linked list, reverse the list, and return *the reversed list*.

   

  **Example 1:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grjrfu2ilbj30f2066mxe.jpg)

  ```
  Input: head = [1,2,3,4,5]
  Output: [5,4,3,2,1]
  ```

  **Example 2:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grjrfvd6loj3052066jrb.jpg)

  ```
  Input: head = [1,2]
  Output: [2,1]
  ```

  **Example 3:**

  ```
  Input: head = []
  Output: []
  ```

   

  **Constraints:**

  - The number of nodes in the list is the range `[0, 5000]`.
  - `-5000 <= Node.val <= 5000`

   

  **Follow up:** A linked list can be reversed either iteratively or recursively. Could you implement both?

---

## 解题思路

---

### 使用方法：遍历

---

###题目关键信息

给你单链表的头节点 `head` ，请你反转链表，并返回反转后的链表。

---

### 解题步骤

设置三个指针 pre, cur, next;

依次翻转直到cur指向null

---

### 图解

![img](https://tva1.sinaimg.cn/large/008i3skNgy1grjrota51og30zk0k0161.gif)

---

### 代码实现

#### 双指针

```java
        while(cur != end){
            next = cur.next;
            // 逐个结点反转
            cur.next = pre;
            // 更新指针位置
            pre = cur;
            cur = next;
        }
```

#### 最终代码

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode pre, cur, next;
        pre = null; cur = head; next = head;
        
        while(cur != end){
            next = cur.next;
            // 逐个结点反转
            cur.next = pre;
            // 更新指针位置
            pre = cur;
            cur = next;
        }
        // 返回反转后的头结点
        return pre;
    }
}
```

