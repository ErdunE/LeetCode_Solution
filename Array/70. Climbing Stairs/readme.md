## 70. Climbing Stairs

#### 中文题目链接[70. 爬楼梯](https://leetcode-cn.com/problems/climbing-stairs/)

#### 英文题目链接[70. Climbing Stairs](https://leetcode.com/problems/climbing-stairs/)

- You are climbing a staircase. It takes `n` steps to reach the top.

  Each time you can either climb `1` or `2` steps. In how many distinct ways can you climb to the top?

   

  **Example 1:**

  ```
  Input: n = 2
  Output: 2
  Explanation: There are two ways to climb to the top.
  1. 1 step + 1 step
  2. 2 steps
  ```

  **Example 2:**

  ```
  Input: n = 3
  Output: 3
  Explanation: There are three ways to climb to the top.
  1. 1 step + 1 step + 1 step
  2. 1 step + 2 steps
  3. 2 steps + 1 step
  ```

   

  **Constraints:**

  - `1 <= n <= 45`

---

## 解题思路

---

### 使用方法：动态规划

---

###题目关键信息

爬楼梯，n个台阶到楼顶

每次爬 1 或者 2个台阶 

求有多少种方法可以爬到楼顶

---

### 解题步骤

爬第n阶楼梯的方法数量，等于 2 部分之和

1. 爬上 n-1 阶楼梯的方法数量。因为再爬1阶就能到第n阶
2. 爬上 n-2 阶楼梯的方法数量，因为再爬2阶就能到第n阶

所以我们得到公式 dp[n] = dp[n-1] + dp[n-2]
同时需要初始化 dp[0]=1和 dp[1]=1

----

### 图解

![image-20210609183147596](https://tva1.sinaimg.cn/large/008i3skNgy1grcruf81pkj30et04mq2y.jpg)

![image-20210609183159249](https://tva1.sinaimg.cn/large/008i3skNgy1grcrum90v9j30eq048t8q.jpg)

![image-20210609183209832](https://tva1.sinaimg.cn/large/008i3skNgy1grcrust0jpj30es04kq2z.jpg)

![image-20210609183219374](https://tva1.sinaimg.cn/large/008i3skNgy1grcruyf7nnj30et04d0st.jpg)

---

### 代码实现

#### 动态规划

```java
int[] dp = new int[n + 1];
        dp[0] = 1;
        dp[1] = 1;
        
        for(int i = 2 ; i <= n ; i++){
            dp[i] = dp[i-1] + dp[i-2];
        }
```

#### 最终代码

```java
class Solution {
    public int climbStairs(int n) {
        if(n == 0){
            return 0;
        }
        if(n == 1){
            return 1;
        }
        
        int[] dp = new int[n + 1];
        dp[0] = 1;
        dp[1] = 1;
        
        for(int i = 2 ; i <= n ; i++){
            dp[i] = dp[i-1] + dp[i-2];
        }
        
        return dp[n];
    }
}
```

