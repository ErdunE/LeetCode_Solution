## 238. Product of Array Except Self

#### 中文题目链接[238. 除自身以外数组的乘积](https://leetcode-cn.com/problems/product-of-array-except-self/)

#### 英文题目链接[238. Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)

- Given an integer array `nums`, return *an array* `answer` *such that* `answer[i]` *is equal to the product of all the elements of* `nums` *except* `nums[i]`.

  The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.

  You must write an algorithm that runs in `O(n)` time and without using the division operation.

   

  **Example 1:**

  ```
  Input: nums = [1,2,3,4]
  Output: [24,12,8,6]
  ```

  **Example 2:**

  ```
  Input: nums = [-1,1,0,-3,3]
  Output: [0,0,9,0,0]
  ```

   

  **Constraints:**

  - `2 <= nums.length <= 105`
  - `-30 <= nums[i] <= 30`
  - The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.

   

  **Follow up:** Can you solve the problem in `O(1) `extra space complexity? (The output array **does not** count as extra space for space complexity analysis.)

---

## 解题思路

---

### 使用方法：遍历

---

###题目关键信息

长度为 *n* 的整数数组 `nums`， *n* > 1

返回一个数组 该数组[i] 等于 nums 中除 nums[i] 之外的其余个元素的乘积

---

### 解题步骤

创建一个空数组`res`用来存储最终结果

将`res`数组列成乘积形式，不同的n组成每行内容，形成一个矩阵

我们可以发现矩阵`主对角线` 全部为 1（当前数字不相乘，等价为乘 1）

分别计算矩阵的 `下三角` 和 `上三角`，并且在计算过程中储存过程值

---

### 图解

![image-20210613145212100](https://tva1.sinaimg.cn/large/008i3skNgy1grh7z8j8ulj30fa0a00t1.jpg)

---

### 代码实现

#### 遍历

```java
// 分别计算矩阵的 `下三角` 和 `上三角`，并且在计算过程中储存过程值
        for(int i = 0 ; i < nums.length ; i++){
            res[i] = p;
            p = nums[i] * p;
        }
        
        for(int i = nums.length - 1 ; i > 0 ; i--){
            q = nums[i] * q;
            res[i - 1] = res[i - 1] * q;
        }
```

#### 最终代码

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        // 创建一个空数组res用来存储最终结果
        int[] res = new int[nums.length]; 
        // 设置两个变量 值为1 运算过程中排除自己
        int p = 1, q = 1; 
        
        // 分别计算矩阵的 `下三角` 和 `上三角`，并且在计算过程中储存过程值
        for(int i = 0 ; i < nums.length ; i++){
            res[i] = p;
            p = nums[i] * p;
        }
        
        for(int i = nums.length - 1 ; i > 0 ; i--){
            q = nums[i] * q;
            res[i - 1] = res[i - 1] * q;
        }
        
        return res;
    }
}
```

