## 118. Pascal's Triangle

#### 中文题目链接[118. 杨辉三角](https://leetcode-cn.com/problems/pascals-triangle/)

#### 英文题目链接[118. Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/)

- Given an integer `numRows`, return the first numRows of **Pascal's triangle**.

  In **Pascal's triangle**, each number is the sum of the two numbers directly above it as shown:

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grdlxwva8vg307806o3z0.gif)

   

  **Example 1:**

  ```
  Input: numRows = 5
  Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
  ```

  **Example 2:**

  ```
  Input: numRows = 1
  Output: [[1]]
  ```

   

  **Constraints:**

  - `1 <= numRows <= 30`

---

## 解题思路

---

### 使用方法：迭代

---

###题目关键信息

非负整数 numRows,代表该三角的行数

每个数是它左上角和右上角的和

---

### 解题步骤

创建result数组存储最终结果

创建row数组存储每一行的最终结果

设置循环 

如果是每行的开头和结尾，直接设置为1

或者获取上一行的值，然后获得它的下标

把每一行rows的结果添加进最终结果中

---

### 图解



---

### 代码实现

#### 迭代

```java
for(int i = 0; i < numRows ; i++){
            // 创建row数组存储每一行的最终结果
            List<Integer> rows = new ArrayList<>();
            
            // 总列数
            for(int j = 0; j <= i ; j++){
                
                // 如果是每行的开头和结尾，直接设置为1
                if(j == 0 || j == i){
                    rows.add(1);
                }
                // 或者获取上一行的值，然后获得它的下标
                // j 是不会等于 0 的 因为上面已经判断过了，同样也不用担心越界情况，因为如果是最后一个同样不会被执行
                else
                {
                    rows.add(result.get(i-1).get(j-1) + result.get(i-1).get(j));
                }
            }
            //把每一行rows的结果添加进最终结果中
            result.add(rows);
        }
```

#### 最终代码

```java
class Solution {
    public List<List<Integer>> generate(int numRows) {
        // 创建result数组存储最终结果
        List<List<Integer>> result = new ArrayList<>();
        
        // 总行数
        for(int i = 0; i < numRows ; i++){
            // 创建row数组存储每一行的最终结果
            List<Integer> rows = new ArrayList<>();
            
            // 总列数
            for(int j = 0; j <= i ; j++){
                
                // 如果是每行的开头和结尾，直接设置为1
                if(j == 0 || j == i){
                    rows.add(1);
                }
                // 或者获取上一行的值，然后获得它的下标
                // j 是不会等于 0 的 因为上面已经判断过了，同样也不用担心越界情况，因为如果是最后一个同样不会被执行
                else
                {
                    rows.add(result.get(i-1).get(j-1) + result.get(i-1).get(j));
                }
            }
            //把每一行rows的结果添加进最终结果中
            result.add(rows);
        }
        
        return result;
    }
}
```

