## 1 Two Sum 两数之和

题目链接 https://leetcode.com/problems/two-sum/

###暴力解法 线性解法

定义数组

遍历数组

​	如果找到了num2 == target-num1

​		判定是不是它本身

​		如果是继续遍历

​		如果不是就找num2的索引

​		返回num1 num2的索引

返回[] 

```python
  class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        j = 0  
      
        for i in range(len(nums)):
              if(target - nums[i]) in nums:
                  if(nums.count(target - nums[i]) == 1) & (target - nums[i] == nums[i]):
                      continue
                  else:
                      j = nums.index(target - nums[i],i+1)
                      return [i,j]
          return []
```



```
Success

[Details ](https://leetcode.com/submissions/detail/636795877/)

Runtime: 647 ms, faster than 46.83% of Python online submissions for Two Sum.

Memory Usage: 14.1 MB, less than 96.62% of Python online submissions for Two Sum.

Next challenges:
```



##双指针

循环从第一个数字开始

​	当左指针在i的位置

​	循环从第i+1个开始到最后一个

​			找到了目标值

​			返回左右指针的索引

返回空

```python
def twoSum(self, nums: List[int], target: int) -> List[int]:
    for i in range(len(nums)):
        for j in range(i + 1, len(nums)):
            if nums[j] == target - nums[i]:
                return [i, j]
    return []
```



```
Success

[Details ](https://leetcode.com/submissions/detail/636829840/)

Runtime: 5710 ms, faster than 11.73% of Python3 online submissions for Two Sum.

Memory Usage: 14.8 MB, less than 85.10% of Python3 online submissions for Two Sum.
```



### Hashmap(不确定python叫啥) 哈希表 


先创建一个hashmap 将数组中的所有数字放进去

循环从第一个数字开始

​	如果目标-数字1的结果 能在hashmap中找到

​		判定是否是自己

​		返回左右指针的索引

返回空

```python
    class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        hashmap = {x: i for i, x in enumerate(nums)}
        for i in range(len(nums)):
            num1 = nums[i]
            if(target - num1) in hashmap:
                num2_index = hashmap[target - num1]
                if(num2_index != i):
                    return[i,num2_index]
        return []
```


​                

```
Success
Details 
Runtime: 49 ms, faster than 78.06% of Python online submissions for Two Sum.
Memory Usage: 14.3 MB, less than 72.32% of Python online submissions for Two Sum.

```

​    

### 字典 dict

设置一个字典

循环从第一个数字开始

​	如果目标-数字1的结果能在字典中找到

​		输出字典中数字2的索引

​		返回返回左右指针的索引

​	如果没有在字典中找到目标-数字1的结果 将数字1和它的索引放进字典

返回空



```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        num_index_map = dict()
        for i in range(len(nums)):
                x = nums[i]
                if (target - x) in num_index_map:
                    index = num_index_map[target - x]
                    return [i, index]
                num_index_map[x] = i

            return []
```



```
Success

[Details ](https://leetcode.com/submissions/detail/636836957/)

Runtime: 91 ms, faster than 59.59% of Python3 online submissions for Two Sum.

Memory Usage: 15.3 MB, less than 50.57% of Python3 online submissions for Two Sum.
```

