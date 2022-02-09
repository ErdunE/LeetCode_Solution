## 142. Linked List Cycle II

### 快慢针(双指针)

![image-20220208203754876](https://tva1.sinaimg.cn/large/008i3skNgy1gz70fcaj4mj316u0fct9q.jpg)

相遇时候走的节点数

Slow   x + y
fast指针走过的节点数： x + y + n (y + z)

fast走的速度是 slow 的二倍



 x + y + n (y + z) = 2(x + y)

x+y+ny+nz = 2x + 2y

ny + nz = 2x + 2y - x - y

ny + nz = x + y

x = (n-1)y + nz

n如果 = 1

x = z



设置快慢针 起点在head

设置while循环 条件 fast 和fast.next 不为空

​	新慢针 = 慢针走一步

​	新快针 = 快针走两步

​	如果相遇了

​		设置一个新的针叫A = head

​		设置一个新的针叫B = slow

​		设置while循环 A ！=B

​			新A = A+1

​			新B = B+1

​		retrun A		

返回 None



```python
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
		slow = head
    fast = head
    
    while fast and fast.next:
        
        slow = slow.next
        fast = fast.next.next
        
        if slow == fast:
            
            A = head
            B = slow
            
            while A!=B:
                A = A.next
                B = B.next
                
            return A
    
    return None
```



### 哈希表

创建一个哈希表

设置慢针等于head

设置while循环 条件 慢针不空或者慢针下一个不空 就一直循环

​		如果再哈希表中找到了当前慢针

​				返回 慢针的值

​		把当前慢针的值加入到哈希表中

​		新慢针 = 慢针的下一个

返回None        

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        Hashmap = set()
        slow = head
        while slow and slow.next:
            if slow in Hashmap:
                return slow
            Hashmap.add(slow)
            slow = slow.next

        return None
```