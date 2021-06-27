## 22. Generate Parentheses

#### 中文题目链接[22. 括号生成](https://leetcode-cn.com/problems/generate-parentheses/)

#### 英文题目链接[22. Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)

- Given `n` pairs of parentheses, write a function to *generate all combinations of well-formed parentheses*.

   

  **Example 1:**

  ```
  Input: n = 3
  Output: ["((()))","(()())","(())()","()(())","()()()"]
  ```

  **Example 2:**

  ```
  Input: n = 1
  Output: ["()"]
  ```

   

  **Constraints:**

  - `1 <= n <= 8`

---

## 解题思路

---

### 使用方法：递归 + DFS

---

###题目关键信息

数字 `n` 代表生成括号的对数

设计一个函数，用于能够生成所有可能的并且 **有效的** 括号组合。

---

### 解题步骤

当前左右括号都有大于 0 个可以使用的时候，才产生分支；
产生左分支的时候，只看当前是否还有左括号可以使用；
产生右分支的时候，还受到左分支的限制，右边剩余可以使用的括号数量一定得在严格大于左边剩余的数量的时候，才可以产生分支；
在左边和右边剩余的括号数都等于 0的时候结算。

---

### 图解

![LeetCode 第 22 题：“括号生出”题解配图.png](https://tva1.sinaimg.cn/large/008i3skNgy1grxil0yhl0j31hc0u0q9e.jpg)

---

### 代码实现

#### DFS

```java
    private void dfs(String curStr, int left, int right, List<String> res){
        // 因为每一次尝试，都使用新的字符串变量，所以无需回溯
        // 在递归终止的时候，直接把它添加到结果集即可    
        if(left == 0 && right == 0){
            res.add(curStr);
            return;
        }
        // 剪枝（如图，左括号可以使用的个数严格大于右括号可以使用的个数，才剪枝，注意这个细节）
        if(left > right){
            return;
        }
            
        if(left > 0){
            dfs(curStr + "(", left - 1, right, res);
        }
            
        if(right > 0){
            dfs(curStr + ")", left , right - 1, res);
        }
    } 
```

#### 最终代码

```java
class Solution {
    public List<String> generateParenthesis(int n) {
        
        // 创建res保存结果
        List<String> res = new ArrayList<>();
        // 特判
        if(n == 0){
            return res;
        }
        // 执行深度优先遍历，搜索可能的结果
        dfs("", n , n , res);
        // 返回结果
        return res;         
    }
    
    /**
     *  curStr 当前递归得到的结果
     *  left   左括号还有几个可以使用
     *  right  右括号还有几个可以使用
     *  res    结果集
     */

    private void dfs(String curStr, int left, int right, List<String> res){
        // 因为每一次尝试，都使用新的字符串变量，所以无需回溯
        // 在递归终止的时候，直接把它添加到结果集即可    
        if(left == 0 && right == 0){
            res.add(curStr);
            return;
        }
        // 剪枝（如图，左括号可以使用的个数严格大于右括号可以使用的个数，才剪枝，注意这个细节）
        if(left > right){
            return;
        }
            
        if(left > 0){
            dfs(curStr + "(", left - 1, right, res);
        }
            
        if(right > 0){
            dfs(curStr + ")", left , right - 1, res);
        }
    }  
}
```

