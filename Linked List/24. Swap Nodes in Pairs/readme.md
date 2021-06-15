##24. Swap Nodes in Pairs

#### 中文题目链接[24. 两两交换链表中的节点](https://leetcode-cn.com/problems/swap-nodes-in-pairs/)

#### 英文题目链接[24. Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/)

-  Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

   

  **Example 1:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grin4qk9nsj30bq066aa7.jpg)

  ```
  Input: head = [1,2,3,4]
  Output: [2,1,4,3]
  ```

  **Example 2:**

  ```
  Input: head = []
  Output: []
  ```

  **Example 3:**

  ```
  Input: head = [1]
  Output: [1]
  ```

   

  **Constraints:**

  - The number of nodes in the list is in the range `[0, 100]`.
  - `0 <= Node.val <= 100`

---

## 解题思路

---

### 使用方法：递归

---

###题目关键信息

给一个链表

两两交换其中相邻的节点

返回交换后的链表

要求不能只是更换节点的值，要实际的进行节点的交换

---

### 解题步骤

返回值：交换完成的子链表
调用单元：设需要交换的两个点为 head 和 next，head 连接后面交换完成的子链表，next 连接 head，完成交换
终止条件：head 为空指针或者 next 为空指针，也就是当前无节点或者只有一个节点，无法进行交换

---

### 图解

![image-20210615173619680](https://tva1.sinaimg.cn/large/008i3skNgy1grjnym7jpej30ez06m0t7.jpg)

![image-20210615173630217](https://tva1.sinaimg.cn/large/008i3skNgy1grjnyqcsf2j30eu05pmxl.jpg)

![image-20210615173645328](https://tva1.sinaimg.cn/large/008i3skNgy1grjnyzqo1jj30ex06jmxv.jpg)

![image-20210615173656641](https://tva1.sinaimg.cn/large/008i3skNgy1grjnz6qkiaj30ez05b0t1.jpg)

![image-20210615173709648](https://tva1.sinaimg.cn/large/008i3skNgy1grjnzeopd4j30f1073js5.jpg)

---

### 代码实现

#### 递归

```java
while(temp.next != null && temp.next.next != null){
            ListNode start = temp.next;
            ListNode end = temp.next.next;
            temp.next = end;
            start.next = end.next;
            end.next = start;
            temp = start;
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
    public ListNode swapPairs(ListNode head) {
        ListNode res = new ListNode(-1);
        ListNode temp = res;
        res.next = head;
        
        while(temp.next != null && temp.next.next != null){
            ListNode start = temp.next;
            ListNode end = temp.next.next;
            temp.next = end;
            start.next = end.next;
            end.next = start;
            temp = start;
        }
        
        return res.next;
        
    }
}
```

