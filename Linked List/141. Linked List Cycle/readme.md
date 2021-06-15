## 141. Linked List Cycle

#### 中文题目链接[141. 环形链表](https://leetcode-cn.com/problems/linked-list-cycle/)

#### 英文题目链接[141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)

- Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

  There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to. **Note that `pos` is not passed as a parameter**.

  Return `true` *if there is a cycle in the linked list*. Otherwise, return `false`.

   

  **Example 1:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grjpu8rb1oj60er04r0sr02.jpg)

  ```
  Input: head = [3,2,0,-4], pos = 1
  Output: true
  Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).
  ```

  **Example 2:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grjpu9migwj305l02xglg.jpg)

  ```
  Input: head = [1,2], pos = 0
  Output: true
  Explanation: There is a cycle in the linked list, where the tail connects to the 0th node.
  ```

  **Example 3:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grjpuakskuj301t01twe9.jpg)

  ```
  Input: head = [1], pos = -1
  Output: false
  Explanation: There is no cycle in the linked list.
  ```

   

  **Constraints:**

  - The number of the nodes in the list is in the range `[0, 104]`.
  - `-105 <= Node.val <= 105`
  - `pos` is `-1` or a **valid index** in the linked-list.

   

  **Follow up:** Can you solve it using `O(1)` (i.e. constant) memory?

---

## 解题思路

---

### 使用方法：双指针

---

###题目关键信息

给一个链表，判断链表中是否有环

如果链表中有某个节点，可以通过连续跟踪 next 指针再次到达，则链表中存在环。 为了表示给定链表中的环，我们使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。注意：pos 不作为参数进行传递，仅仅是为了标识链表的实际情况。

如果链表中存在环，则返回 true 。 否则，返回 false 。

---

### 解题步骤

设置快慢指针

慢指针每次走一步，快指针每次走两步

如果相遇即为有环

否则没环

---

### 图解

![img](https://tva1.sinaimg.cn/large/008i3skNgy1grjqfwk2bsj30uo0j0q3q.jpg)

---

### 代码实现

#### 双指针

```java
        while(fast != null && fast.next != null){
            //慢指针每次走一步
            slow = slow.next;
            //快指针每次走两步
            fast = fast.next.next;
            //如果相遇，说明有环，直接返回true
            if(slow == fast){
                return true;
            }
        }
```

#### 最终代码

```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        if(head == null){
            return false;
        }
        //快慢两个指针
        ListNode slow = head;
        ListNode fast = head;
        
        while(fast != null && fast.next != null){
            //慢指针每次走一步
            slow = slow.next;
            //快指针每次走两步
            fast = fast.next.next;
            //如果相遇，说明有环，直接返回true
            if(slow == fast){
                return true;
            }
        }
        //否则就是没环
        return false;
    }
}
```

