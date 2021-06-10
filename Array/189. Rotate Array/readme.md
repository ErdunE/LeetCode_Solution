## 189. Rotate Array

#### 中文题目链接[189. 旋转数组](https://leetcode-cn.com/problems/rotate-array/)

#### 英文题目链接[189. Rotate Array](https://leetcode.com/problems/rotate-array/)

- Given an array, rotate the array to the right by `k` steps, where `k` is non-negative.

   

  **Example 1:**

  ```
  Input: nums = [1,2,3,4,5,6,7], k = 3
  Output: [5,6,7,1,2,3,4]
  Explanation:
  rotate 1 steps to the right: [7,1,2,3,4,5,6]
  rotate 2 steps to the right: [6,7,1,2,3,4,5]
  rotate 3 steps to the right: [5,6,7,1,2,3,4]
  ```

  **Example 2:**

  ```
  Input: nums = [-1,-100,3,99], k = 2
  Output: [3,99,-1,-100]
  Explanation: 
  rotate 1 steps to the right: [99,-1,-100,3]
  rotate 2 steps to the right: [3,99,-1,-100]
  ```

   

  **Constraints:**

  - `1 <= nums.length <= 105`
  - `-231 <= nums[i] <= 231 - 1`
  - `0 <= k <= 105`

   

  **Follow up:**

  - Try to come up with as many solutions as you can. There are at least **three** different ways to solve this problem.
  - Could you do it in-place with `O(1)` extra space?

---

## 解题思路

---

### 使用方法：遍历+翻转

---

###题目关键信息

一个数组 nums

将数组中的元素向右移动k个位置

k为非负数

---

### 解题步骤

写一个翻转函数

整体旋转

旋转第一个数到第k个数字

旋转第k+1个数字到最后

---

### 图解

![image-20210610195400210](https://tva1.sinaimg.cn/large/008i3skNgy1grdzu9sjjej30f201dmx3.jpg)

![image-20210610195411513](https://tva1.sinaimg.cn/large/008i3skNgy1grdzugu0xwj30f202tq35.jpg)

![image-20210610195422678](https://tva1.sinaimg.cn/large/008i3skNgy1grdzung0e3j30ex06b74w.jpg)

![image-20210610195434681](https://tva1.sinaimg.cn/large/008i3skNgy1grdzuv0swpj30ez062wf5.jpg)

![image-20210610195445201](https://tva1.sinaimg.cn/large/008i3skNgy1grdzv1ghzaj30ed062wew.jpg)

---

### 代码实现

#### 迭代

```java
    // 旋转函数
    public void reverse(int[] nums, int start, int end){
        while(start < end){
            int tmp = nums[start];
            nums[start] = nums[end];
            nums[end] = tmp;
            start += 1;
            end -= 1;
        }
    }
```

#### 最终代码

```java
class Solution {
    public void rotate(int[] nums, int k) {
        // 特判，如果k的值大于nums的元素数量
        k %= nums.length;
        // 整体旋转
        reverse(nums, 0, nums.length - 1);
        // 旋转第一个数到第k个数字
        reverse(nums, 0, k - 1);
        // 旋转第k+1个数字到最后
        reverse(nums, k, nums.length - 1);
         
    }
    // 旋转函数
    public void reverse(int[] nums, int start, int end){
        while(start < end){
            int tmp = nums[start];
            nums[start] = nums[end];
            nums[end] = tmp;
            start += 1;
            end -= 1;
        }
    }
}
```

