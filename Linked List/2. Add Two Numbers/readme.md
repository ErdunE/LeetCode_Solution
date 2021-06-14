## 2. Add Two Numbers

#### 中文题目链接[2. 两数相加](https://leetcode-cn.com/problems/add-two-numbers/)

#### 英文题目链接[2. Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)

- You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order**, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

  You may assume the two numbers do not contain any leading zero, except the number 0 itself.

   

  **Example 1:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grij27u8flj30df09i3yr.jpg)

  ```
  Input: l1 = [2,4,3], l2 = [5,6,4]
  Output: [7,0,8]
  Explanation: 342 + 465 = 807.
  ```

  **Example 2:**

  ```
  Input: l1 = [0], l2 = [0]
  Output: [0]
  ```

  **Example 3:**

  ```
  Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
  Output: [8,9,9,9,0,0,0,1]
  ```

   

  **Constraints:**

  - The number of nodes in each linked list is in the range `[1, 100]`.
  - `0 <= Node.val <= 9`
  - It is guaranteed that the list represents a number that does not have leading zeros.

---

## 解题思路

---

### 使用方法：遍历

---

###题目关键信息

两个非空链表，表示两个非负整数

每位数字都是按照逆序排序的

每个节点只能存储一位数字

将两数相加，返回一个链表

---

### 解题步骤

创建新的链表存储结果

创建变量进位值为 carry

设置两个链表当前位置的数字为 x，y 

和为 sum

则 sum = x + y + carry

新的进位值 carry = sum / 10

答案链表相应位置的数字为 sum % 10

如果两个链表的长度不同，就在短链表的末尾补0

---

### 图解

---

### 代码实现

#### 遍历

```java
        while(l1 != null || l2 != null || carry > 0){
            // 设置两个链表当前位置的数字为 x，y
            // 如果两个链表的长度不同，就在短链表的末尾补0
            int x = l1 == null ? 0 : l1.val;
            int y = l2 == null ? 0 : l2.val;
            // 和为 sum
            // 则 sum = x + y + carry
            int sum = x + y + carry;
            // 新的进位值 carry = sum / 10
            carry = sum / 10;
            // 答案链表相应位置的数字为 sum % 10
            cur.next = new ListNode(sum % 10);
            cur = cur.next;
            
            if(l1 != null){
                l1 = l1.next;
            }
            
            if(l2 != null){
                l2 = l2.next;
            }
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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        // 创建新的链表存储结果
        ListNode res = new ListNode(0);
        // 创建临时链表
        ListNode cur = res;
        // 创建变量进位值为 carry
        int carry = 0;
        
        
        while(l1 != null || l2 != null || carry > 0){
            // 设置两个链表当前位置的数字为 x，y
            // 如果两个链表的长度不同，就在短链表的末尾补0
            int x = l1 == null ? 0 : l1.val;
            int y = l2 == null ? 0 : l2.val;
            // 和为 sum
            // 则 sum = x + y + carry
            int sum = x + y + carry;
            // 新的进位值 carry = sum / 10
            carry = sum / 10;
            // 答案链表相应位置的数字为 sum % 10
            cur.next = new ListNode(sum % 10);
            cur = cur.next;
            
            if(l1 != null){
                l1 = l1.next;
            }
            
            if(l2 != null){
                l2 = l2.next;
            }
        }
        
        return res.next;
    }
}
```

