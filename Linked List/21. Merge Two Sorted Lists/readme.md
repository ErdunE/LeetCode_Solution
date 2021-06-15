## 21. Merge Two Sorted Lists

#### 中文题目链接[21. 合并两个有序链表](https://leetcode-cn.com/problems/merge-two-sorted-lists/)

#### 英文题目链接[21. Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

- Merge two sorted linked lists and return it as a **sorted** list. The list should be made by splicing together the nodes of the first two lists.

   

  **Example 1:**

  

  ```
  Input: l1 = [1,2,4], l2 = [1,3,4]
  Output: [1,1,2,3,4,4]
  ```

  **Example 2:**

  ```
  Input: l1 = [], l2 = []
  Output: []
  ```

  **Example 3:**

  ```
  Input: l1 = [], l2 = [0]
  Output: [0]
  ```

   

  **Constraints:**

  - The number of nodes in both lists is in the range `[0, 50]`.
  - `-100 <= Node.val <= 100`
  - Both `l1` and `l2` are sorted in **non-decreasing** order.

---

## 解题思路

---

### 使用方法：迭代

---

###题目关键信息

两个升序链表

合并成一个新的升序链接并返回

---

### 解题步骤

创建新的链表存储结果

创建一个新的指针

当 `l1` 和 `l2` 都不是空链表时

判断 `l1` 和 `l2` 哪一个链表的头节点的值更小

将较小值的节点添加到结果里

当一个节点被添加到结果里之后，将对应链表中的节点向后移一位

合并后 l1 和 l2 最多只有一个还未被合并完，我们直接将链表末尾指向未合并完的链表即可

---

### 图解



---

### 代码实现

#### 迭代

```java
				// 当l1和l2都不是空链表时
        // 判断l1和l2哪一个链表的头节点的值更小
        // 将较小值的节点添加到结果里
        // 当一个节点被添加到结果里之后，将对应链表中的节点向后移一位
        while(l1 != null && l2 != null){
            if(l1.val <= l2.val){
                point.next = l1;
                l1 = l1.next;
            }
            else{
                point.next = l2;
                l2 = l2.next;
            }
            
            // 合并后 l1 和 l2 最多只有一个还未被合并完，我们直接将链表末尾指向未合并完的链表即可
            point = point.next;
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
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        // 创建新的链表存储结果
        ListNode res = new ListNode(-1); 
        // 创建一个新的指针
        ListNode point = res;
        
        // 当l1和l2都不是空链表时
        // 判断l1和l2哪一个链表的头节点的值更小
        // 将较小值的节点添加到结果里
        // 当一个节点被添加到结果里之后，将对应链表中的节点向后移一位
        while(l1 != null && l2 != null){
            if(l1.val <= l2.val){
                point.next = l1;
                l1 = l1.next;
            }
            else{
                point.next = l2;
                l2 = l2.next;
            }
            
            // 合并后 l1 和 l2 最多只有一个还未被合并完，我们直接将链表末尾指向未合并完的链表即可
            point = point.next;
        }

                
        point.next = l1 == null ? l2 : l1;
        
        return res.next;
    }
}
```

