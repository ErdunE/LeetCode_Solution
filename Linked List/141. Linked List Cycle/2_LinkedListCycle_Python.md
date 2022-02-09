##  141. Linked List Cycle

题目链接：https://leetcode.com/problems/linked-list-cycle/

### 快慢针(双指针)

先做一个判定，如果没有第一个node，或者没有第二node

​	返回 false

定义慢针 起点在头的位置

定义快针 起点在头的下一个位置

while 循环 条件为 快针不等于慢针 就一直循环

​	如果快针没有了，或者快针的下一步没有了

​		返回false

​	新慢针 = 慢针走一步

​	新快针 = 快针走两步

返回true

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
          
  	if not head or not head.next:
        return False
    
    slow = head
    fast = head.next
    
    while slow != fast:
        if not fast or not fast.next:
            return False
        
        slow = slow.next
        fast = fast.next.next
    
    return True
```

​	

### 哈希表

先设置一个空的哈希表

循环 head (里面有值/node 就等于true )

​	如果哈希表里面有head

​		返回True

​	将head加入到哈希表中

​	head 等于 head的下一个值

返回False
        

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
    Hashmap = set()
    
    while head:
        if head in Hashmap:
            return True
        Hashmap.add(head)
        head = head.next
        
    return False
```