## 88. Merge Sorted Array

#### 中文题目链接[88. 合并两个有序数组](https://leetcode-cn.com/problems/merge-sorted-array/)

#### 英文题目链接[88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)

- You are given two integer arrays `nums1` and `nums2`, sorted in **non-decreasing order**, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively.

  **Merge** `nums1` and `nums2` into a single array sorted in **non-decreasing order**.

  The final sorted array should not be returned by the function, but instead be *stored inside the array* `nums1`. To accommodate this, `nums1` has a length of `m + n`, where the first `m` elements denote the elements that should be merged, and the last `n` elements are set to `0` and should be ignored. `nums2` has a length of `n`.

   

  **Example 1:**

  ```
  Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
  Output: [1,2,2,3,5,6]
  Explanation: The arrays we are merging are [1,2,3] and [2,5,6].
  The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.
  ```

  **Example 2:**

  ```
  Input: nums1 = [1], m = 1, nums2 = [], n = 0
  Output: [1]
  Explanation: The arrays we are merging are [1] and [].
  The result of the merge is [1].
  ```

  **Example 3:**

  ```
  Input: nums1 = [0], m = 0, nums2 = [1], n = 1
  Output: [1]
  Explanation: The arrays we are merging are [] and [1].
  The result of the merge is [1].
  Note that because m = 0, there are no elements in nums1. The 0 is only there to ensure the merge result can fit in nums1.
  ```

   

  **Constraints:**

  - `nums1.length == m + n`
  - `nums2.length == n`
  - `0 <= m, n <= 200`
  - `1 <= m + n <= 200`
  - `-109 <= nums1[i], nums2[j] <= 109`

---

## 解题思路

---

### 使用方法：遍历

---

###题目关键信息

两个有序整数数组 `nums1` 和 `nums2`

将 `nums2` 合并到 `nums1` 中*，*使 `nums1` 成为一个有序数组

初始化 `nums1` 和 `nums2` 的元素数量分别为 `m` 和 `n`

假设 `nums1` 的空间大小等于 `m + n`

---

### 解题步骤

从后向前遍历

设置指针 len1 和 len2 分别指向 nums1 和 nums2 的有数字尾部

从尾部值开始比较遍历

同时设置指针 len 指向 nums1 的最末尾

每次遍历比较值大小之后，则进行填充

### 图解

![image-20210609205331696](https://tva1.sinaimg.cn/large/008i3skNgy1grcvxvsqlfj30f406kaad.jpg)![image-20210609205344605](https://tva1.sinaimg.cn/large/008i3skNgy1grcvy4kg06j30ev06k3yt.jpg)![image-20210609205354763](https://tva1.sinaimg.cn/large/008i3skNgy1grcvyajrs9j30et06lwes.jpg)![image-20210609205405471](https://tva1.sinaimg.cn/large/008i3skNgy1grcvyhdi26j30eu06lwer.jpg)

---

### 代码实现

#### 遍历

```java
while(len2 >= 0){
            // 如果指针1 小于0 正面nums1里面的值已经全部排好序 将剩下的nums2的值直接放进去就可以
            if(len1 < 0){
                while(len2 >= 0){
                    nums1[len--] = nums2[len2--];
                }
                return;
            }
            
            // 将nums1中的值 和 nums2中的值 进行比较
            // nums1中的值大  插入 nums1 最后位置
            if(nums1[len1] > nums2[len2]){
                nums1[len--] = nums1[len1--];
            }
            // nums2中的值大  插入 nums1 最后位置
            else{
                nums1[len--] = nums2[len2--]; 
            }
        }  
```

#### 最终代码

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int len1 = m - 1; // 指针1 指向nums1 有效的 的最后一个元素
        int len2 = n - 1; // 指针2 指向nums2 有效的 的最后一个元素
        int len = m + n - 1; // 指针3 指向nums1 的最后一个元素
        
        while(len2 >= 0){
            // 如果指针1 小于0 正面nums1里面的值已经全部排好序 将剩下的nums2的值直接放进去就可以
            if(len1 < 0){
                while(len2 >= 0){
                    nums1[len--] = nums2[len2--];
                }
                return;
            }
            
            // 将nums1中的值 和 nums2中的值 进行比较
            // nums1中的值大  插入 nums1 最后位置
            if(nums1[len1] > nums2[len2]){
                nums1[len--] = nums1[len1--];
            }
            // nums2中的值大  插入 nums1 最后位置
            else{
                nums1[len--] = nums2[len2--]; 
            }
        }  
    }
}
```

