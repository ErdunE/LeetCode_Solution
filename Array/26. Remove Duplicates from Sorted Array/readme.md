## 26. Remove Duplicates from Sorted Array

#### 中文题目链接[26. 删除有序数组中的重复项](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/)

#### 英文题目链接[26. Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

- Given a sorted array *nums*, remove the duplicates [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) such that each element appears only *once* and returns the new length.

  Do not allocate extra space for another array, you must do this by **modifying the input array [in-place](https://en.wikipedia.org/wiki/In-place_algorithm)** with O(1) extra memory.

  **Clarification:**

  Confused why the returned value is an integer but your answer is an array?

  Note that the input array is passed in by **reference**, which means a modification to the input array will be known to the caller as well.

  Internally you can think of this:

  ```
  // nums is passed in by reference. (i.e., without making a copy)
  int len = removeDuplicates(nums);
  
  // any modification to nums in your function would be known by the caller.
  // using the length returned by your function, it prints the first len elements.
  for (int i = 0; i < len; i++) {
      print(nums[i]);
  }
  ```

   

  **Example 1:**

  ```
  Input: nums = [1,1,2]
  Output: 2, nums = [1,2]
  Explanation: Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively. It doesn't matter what you leave beyond the returned length.
  ```

  **Example 2:**

  ```
  Input: nums = [0,0,1,1,1,2,2,3,3,4]
  Output: 5, nums = [0,1,2,3,4]
  Explanation: Your function should return length = 5, with the first five elements of nums being modified to 0, 1, 2, 3, and 4 respectively. It doesn't matter what values are set beyond the returned length.
  ```

   

  **Constraints:**

  - 0 <= nums.length <= 3 * 10^4^
  - -10^4^ <= nums[i] <= 10^4^
  - `nums` is sorted in ascending order.

---

## 解题思路

---

### 使用方法：双指针

---

###题目关键信息

一个已经排序好的数组

原地删除重复出现的元素，不使用额外的数组空间

返回删除后数组的新长度

---

### 解题步骤

首先注意，数组是有序的，即重复的元素一定是相邻的

要求删除重复元素，实际上就是将不重复的元素移动到数组左侧，重复的移动到数组右侧

设置双指针 `left=0, right=1`

比较left和right位置的元素是否相同

如果相等，right后移一位

如果不相等，right的元素复制到left+1的位置上，然后left后移一位

重复上述过程直到right等于数组长度

返回结果p+1

----

### 图解

![image-20210609104105084](https://tva1.sinaimg.cn/large/008i3skNgy1grce8ppsf4j60ag0iggmx02.jpg)

---

### 代码实现

#### 双指针循环

```java
 // 循环 比较left和right位置的元素是否相同
        while(right < nums.length){
            // 如果不相等，right的元素复制到left+1的位置上，然后left后移一位
            if(nums[right] != nums[left]){
                nums[left+1] = nums[right];
                left++;
            }
            // 如果相等，right后移一位
            else{
                right++;
            }
        }
```

#### 最终代码

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        // 特判
        if(nums.length == 0 || nums == null){
            return 0;
        }
        
        // 定义快慢指针
        int left = 0;
        int right = 1;
        
        // 循环 比较left和right位置的元素是否相同
        while(right < nums.length){
            // 如果不相等，right的元素复制到left+1的位置上，然后left后移一位
            if(nums[right] != nums[left]){
                nums[left+1] = nums[right];
                left++;
            }
            // 如果相等，right后移一位
            else{
                right++;
            }
        }
        // 返回结果p+1
        return left+1;
    }
}
```

