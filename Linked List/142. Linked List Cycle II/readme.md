## 142. Linked List Cycle II

#### 中文题目链接[142. 环形链表 II](https://leetcode-cn.com/problems/linked-list-cycle-ii/)

#### 英文题目链接[142. Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)

- Given a linked list, return the node where the cycle begins. If there is no cycle, return `null`.

  There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to. **Note that `pos` is not passed as a parameter**.

  **Notice** that you **should not modify** the linked list.

   

  **Example 1:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grjqj7yhm4j30er04r0sr.jpg)

  ```
  Input: head = [3,2,0,-4], pos = 1
  Output: tail connects to node index 1
  Explanation: There is a cycle in the linked list, where tail connects to the second node.
  ```

  **Example 2:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grjqj6om4gj305l02xglg.jpg)

  ```
  Input: head = [1,2], pos = 0
  Output: tail connects to node index 0
  Explanation: There is a cycle in the linked list, where tail connects to the first node.
  ```

  **Example 3:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grjqj95l7yj301t01twe9.jpg)

  ```
  Input: head = [1], pos = -1
  Output: no cycle
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

给一个链表，返回链表开始入环的第一个节点。如果链表无环，则返回null

---

### 解题步骤

其中【*】为快慢指针首次相遇点，入环前距离为【D】，慢指针入环后走过的距离为【S1】，环剩下距离为【S2】

首次相遇
1.慢指针 S = D + S1
2.快指针 F = D + n(S1 + S2) + S1 其中n>=1,快指针起码走了一圈以上才可能相遇
3.又因为 F = 2S 慢指针走一步，快指针走两步
4.代入1，2 可得 2(D + S1) = D + n(S1 + S2) + S1
各种移项可得 D = (n-1)S1 + nS2 = (n-1)(S1 + S2) + S2
5.其中 n为快指针绕的圈数
n=1 D = S2
n=2 D = 一圈 + S2
n=3 D = 两圈 + S2
.....
所以 n圈+S2就是入环点了
6.人为构造碰撞机会，让快指针重新出发（但这次一次走一步），只要碰撞了，就是入环位置了

---

### 图解

![无标题.jpg](https://tva1.sinaimg.cn/large/008i3skNgy1grjqz9mhvnj30fn07874c.jpg)

---

### 代码实现

#### 双指针

```java
        //获取首次相遇时候，slow的位置
        while(true){
            //如果快指针走到尽头，没环
            if(fast == null || fast.next ==null){
                return null;
            }
            
            fast = fast.next.next;
            slow = slow.next;
            
            if(fast == slow){
                break;
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
    public ListNode detectCycle(ListNode head) {
        ListNode slow = head, fast = head;
        
        //获取首次相遇时候，slow的位置
        while(true){
            //如果快指针走到尽头，没环
            if(fast == null || fast.next ==null){
                return null;
            }
            
            fast = fast.next.next;
            slow = slow.next;
            
            if(fast == slow){
                break;
            }
        }
        //快指针重新出发，相遇位置就是入口位置
        fast = head;
        while(slow != fast){
            slow = slow.next;
            fast = fast.next;
        }
        
        return fast;
    }
}
```

