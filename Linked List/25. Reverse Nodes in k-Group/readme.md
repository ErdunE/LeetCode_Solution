## 25. Reverse Nodes in k-Group

#### 中文题目链接[25. K 个一组翻转链表](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/)

#### 英文题目链接[25. Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/)

- Given a linked list, reverse the nodes of a linked list *k* at a time and return its modified list.

  *k* is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of *k* then left-out nodes, in the end, should remain as it is.

  You may not alter the values in the list's nodes, only nodes themselves may be changed.

   

  **Example 1:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grjo46lvm3j30f2066weq.jpg)

  ```
  Input: head = [1,2,3,4,5], k = 2
  Output: [2,1,4,3,5]
  ```

  **Example 2:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grjo47fbbpj30f2066dg2.jpg)

  ```
  Input: head = [1,2,3,4,5], k = 3
  Output: [3,2,1,4,5]
  ```

  **Example 3:**

  ```
  Input: head = [1,2,3,4,5], k = 1
  Output: [1,2,3,4,5]
  ```

  **Example 4:**

  ```
  Input: head = [1], k = 1
  Output: [1]
  ```

   

  **Constraints:**

  - The number of nodes in the list is in the range `sz`.
  - `1 <= sz <= 5000`
  - `0 <= Node.val <= 1000`
  - `1 <= k <= sz`

   

  **Follow-up:** Can you solve the problem in O(1) extra memory space?

---

## 解题思路

---

### 使用方法：递归

---

###题目关键信息

给一个链表

每k个节点为一组进行翻转

返回翻转后的链表

k是正整数且小于或等于链表的长度

如果节点总数不是k的整数倍，最后剩余的节点保持原有顺序

---

### 解题步骤

写一个翻转方法，参数为a, b

根据k的值将链表分为三个部分即 已翻转部分+带翻转部分+未翻转部分

每次翻转前，确定翻转链表的范围a，b

调用翻转方法

循环上面步骤直到剩余部分小于k

---

### 图解

![img](https://tva1.sinaimg.cn/large/008i3skNgy1grjpigupl8g30zk0k0161.gif)

![k个一组翻转链表.png](https://tva1.sinaimg.cn/large/008i3skNgy1grjpjq7r4fj30lx10stax.jpg)

---

### 代码实现

#### 翻转方法

```java
    // 反转区间 [a, b) 的元素，注意是左闭右开
    public ListNode reverse(ListNode head,ListNode end){
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
    public ListNode reverseKGroup(ListNode head, int k) {
        if(head == null){
            return null;
        }
        // 区间 [a, b) 包含 k 个待反转元素
        ListNode a, b;
        a = b = head;
        
        for(int i = 0; i < k ; i++){
            // 不足 k 个，不需要反转，base case
            if(b == null){
                return head;
            }
            b = b.next;
        }
        // 反转前 k 个元素
        ListNode newHead = reverse(a, b);
        // 递归反转后续链表并连接起来
        a.next = reverseKGroup(b, k);
        
        return newHead;
    }
    // 反转区间 [a, b) 的元素，注意是左闭右开
    public ListNode reverse(ListNode head,ListNode end){
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

