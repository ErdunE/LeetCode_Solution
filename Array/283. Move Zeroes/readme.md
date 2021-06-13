## 283. Move Zeroes

#### 中文题目链接[283. 移动零](https://leetcode-cn.com/problems/move-zeroes/)

#### 英文题目链接[283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)

- Given an integer array `nums`, move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

  **Note** that you must do this in-place without making a copy of the array.

   

  **Example 1:**

  ```
  Input: nums = [0,1,0,3,12]
  Output: [1,3,12,0,0]
  ```

  **Example 2:**

  ```
  Input: nums = [0]
  Output: [0]
  ```

   

  **Constraints:**

  - `1 <= nums.length <= 104`
  - `-231 <= nums[i] <= 231 - 1`

   

  **Follow up:** Could you minimize the total number of operations done?

---

## 解题思路

---

### 使用方法：双指针

---

###题目关键信息

数组nums

将所有数组内的0，移动到数组末尾

同时保持非0元素的相对顺序

---

### 解题步骤

创建两个指针

第一次遍历，将所有非0元素向数组左边挪

第一次遍历完，慢指针的下标，就是最后一个非0元素的下标

第二次遍历的时候，其实位置就设置为慢指针到数组结束，将剩余所有元素赋值为0

---

### 图解

![283_1.gif](https://tva1.sinaimg.cn/large/008i3skNgy1grh8sjpwo9g30zk0k07t7.gif)

---

### 代码实现

#### 双指针

```java
        // 先将所有非0元素依次放到队列前面，left指针记录非0的个数，只要是非0的统统都赋给nums[left]
        for(int i = 0 ; i < nums.length ; i++){
            if(nums[i] != 0){
                nums[left] = nums[i];
                left++;
            }
        }
        // 所有非0元素统计完了，剩下的就都是0了
        // 将所有剩余元素赋值为0
        for(int i = left ; i < nums.length ; i++){
            nums[i] = 0;
        }
```

#### 最终代码

```java
class Solution {
    public void moveZeroes(int[] nums) {
        // 特判
        if(nums.length == 0){
            return;
        }
                 
        int left = 0;
        
        // 先将所有非0元素依次放到队列前面，left指针记录非0的个数，只要是非0的统统都赋给nums[left]
        for(int i = 0 ; i < nums.length ; i++){
            if(nums[i] != 0){
                nums[left] = nums[i];
                left++;
            }
        }
        // 所有非0元素统计完了，剩下的就都是0了
        // 将所有剩余元素赋值为0
        for(int i = left ; i < nums.length ; i++){
            nums[i] = 0;
        }
    }
}
```

