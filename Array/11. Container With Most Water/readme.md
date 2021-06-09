## 11. Container With Most Water

#### 中文题目链接[11. 盛最多水的容器](https://leetcode-cn.com/problems/container-with-most-water/)

#### 英文题目链接[11. Container With Most Water](https://leetcode.com/problems/container-with-most-water/)

- Given `n` non-negative integers a~1~, a~2~, ..., a~n~ , where each represents a point at coordinate (i, a~i~). `n` vertical lines are drawn such that the two endpoints of the line `i` is at (i, a~i~) and `(i, 0)`. Find two lines, which, together with the x-axis forms a container, such that the container contains the most water.

  **Notice** that you may not slant the container.

   

  **Example 1:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grbkk1i4t6j60m90anwep02.jpg)

  ```
  Input: height = [1,8,6,2,5,4,8,3,7]
  Output: 49
  Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.
  ```

  **Example 2:**

  ```
  Input: height = [1,1]
  Output: 1
  ```

  **Example 3:**

  ```
  Input: height = [4,3,2,1,4]
  Output: 16
  ```

  **Example 4:**

  ```
  Input: height = [1,2,1]
  Output: 2
  ```

   

  **Constraints:**

  - `n == height.length`
  - `2 <= n <= 10^5^`
  - `0 <= height[i] <= 10^4^`

---

## 解题思路

---

### 使用方法：双指针

---

###题目关键信息

`n`个非负整数 a~1~，a~2~, ... , a~n~

每个数代表一个点 ( i ,  a~i~ )

n条垂直线，(i, a~i~) and (i, 0)是该线的两个端点

求出其中的两条线，使得它们与 `x` 轴共同构成的容器可以容纳最多的水。

---

### 解题步骤

设置双指针 `left, right` 为容器壁两端

每次选定水槽两板高度较低的一方向中间移动一格，直到左右指针相遇

水槽面积等于 `height(left和right中较短的一方) * (right - left 水槽的宽度)`

记录每一次计算结果，进行对比，保存最大面积值

返回结果

----

### 图解

![image-20210608202614847](https://tva1.sinaimg.cn/large/008i3skNgy1grbpj7o8tzj30ey08odgs.jpg)![image-20210608202628285](https://tva1.sinaimg.cn/large/008i3skNgy1grbpjfejs7j30ew08rt9i.jpg)![image-20210608202648067](https://tva1.sinaimg.cn/large/008i3skNgy1grbpjs4csij30ev08q757.jpg)![image-20210608202700797](https://tva1.sinaimg.cn/large/008i3skNgy1grbpjzytynj30en08nt9j.jpg)![image-20210608202715975](https://tva1.sinaimg.cn/large/008i3skNgy1grbpkawajwj30eq08mgmi.jpg)![image-20210608202734461](https://tva1.sinaimg.cn/large/008i3skNgy1grbpkl514yj30eq08k758.jpg)![image-20210608202746262](https://tva1.sinaimg.cn/large/008i3skNgy1grbpksuh0lj30ep08owff.jpg)![image-20210608202800572](https://tva1.sinaimg.cn/large/008i3skNgy1grbpl14x78j30er08lab0.jpg)

---

### 代码实现

#### 双指针循环

```java
while(left < right){
            // 水槽面积等于 height(left和right中较短的一方) * (right - left 水槽的宽度)
            res = Math.max(res, (right - left) * Math.min(height[left], height[right]));
            // 每次选定水槽两板高度较低的一方向中间移动一格，直到左右指针相遇
            if(height[left] >= height[right]){
                right--;
            }else{
                left++;
            }
        }
```

#### 最终代码

```java
class Solution {
    public int maxArea(int[] height) {
      	// 设置结果变量  
      	int res = 0; 
        
        // 设置左指针
        int left = 0; 
        // 设置右指针
        int right = height.length - 1;
        
        while(left < right){
            // 水槽面积等于 height(left和right中较短的一方) * (right - left 水槽的宽度)
            res = Math.max(res, (right - left) * Math.min(height[left], height[right]));
            // 每次选定水槽两板高度较低的一方向中间移动一格，直到左右指针相遇
            if(height[left] >= height[right]){
                right--;
            }else{
                left++;
            }
        }
        
        return res;
    }
}
```

