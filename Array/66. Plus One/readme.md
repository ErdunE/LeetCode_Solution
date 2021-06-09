## 66. Plus One

#### 中文题目链接[66. 加一](https://leetcode-cn.com/problems/plus-one/)

#### 英文题目链接[66. Plus One](https://leetcode.com/problems/plus-one/)

- Given a **non-empty** array of decimal digits representing a non-negative integer, increment one to the integer.

  The digits are stored such that the most significant digit is at the head of the list, and each element in the array contains a single digit.

  You may assume the integer does not contain any leading zero, except the number 0 itself.

   

  **Example 1:**

  ```
  Input: digits = [1,2,3]
  Output: [1,2,4]
  Explanation: The array represents the integer 123.
  ```

  **Example 2:**

  ```
  Input: digits = [4,3,2,1]
  Output: [4,3,2,2]
  Explanation: The array represents the integer 4321.
  ```

  **Example 3:**

  ```
  Input: digits = [0]
  Output: [1]
  ```

   

  **Constraints:**

  - `1 <= digits.length <= 100`
  - `0 <= digits[i] <= 9`

---

## 解题思路

---

### 使用方法：数组遍历

---

###题目关键信息

一个 非空 整数 数组

在该数的基础上加一

最高位数字在数组首位，最低位数字在数组末尾

数组每个元素只存储单个数字

除整数0外，首尾不会以0开头

---

### 解题步骤

末位不进位

末位进位，但是在中间停止

末位进位，一直进位到首尾，导致结果多出一位

----

### 图解

![image-20210609171633015](https://tva1.sinaimg.cn/large/008i3skNgy1grcpo4nnllj30f6044aa4.jpg)![image-20210609171647682](https://tva1.sinaimg.cn/large/008i3skNgy1grcpodnziej60ez078aao02.jpg)![image-20210609171658446](https://tva1.sinaimg.cn/large/008i3skNgy1grcpok4a6vj30f106m0t6.jpg)

---

### 代码实现

#### 末位不进位，以及末位进位但是在中间停止

```java
for(int i = len - 1; i >= 0 ; i--){
            // 末位不进位
            // 末位进位，但是在中间停止
            digits[i]++;
            digits[i] = digits[i] % 10;
            if(digits[i] != 0){
                return digits;
            }
        }
```

#### 最终代码

```java
class Solution {
    public int[] plusOne(int[] digits) {
        
        int len = digits.length;
        
        for(int i = len - 1; i >= 0 ; i--){
            // 末位不进位
            // 末位进位，但是在中间停止
            digits[i]++;
            digits[i] = digits[i] % 10;
            if(digits[i] != 0){
                return digits;
            }
        }
        // 末位进位，一直进位到首尾，导致结果多出一位
        digits = new int[len + 1];
        digits[0] = 1;
        return digits;
    }
}
```

