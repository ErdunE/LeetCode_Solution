## 119. Pascal's Triangle II

#### 中文题目链接[119. 杨辉三角 II](https://leetcode-cn.com/problems/pascals-triangle-ii/)

#### 英文题目链接[119. Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii/)

- Given an integer `rowIndex`, return the `rowIndexth` (**0-indexed**) row of the **Pascal's triangle**.

  In **Pascal's triangle**, each number is the sum of the two numbers directly above it as shown:

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grdyyagpzzg307806o3z0.gif)

   

  **Example 1:**

  ```
  Input: rowIndex = 3
  Output: [1,3,3,1]
  ```

  **Example 2:**

  ```
  Input: rowIndex = 0
  Output: [1]
  ```

  **Example 3:**

  ```
  Input: rowIndex = 1
  Output: [1,1]
  ```

   

  **Constraints:**

  - `0 <= rowIndex <= 33`

---

## 解题思路

---

### 使用方法：迭代

---

###题目关键信息

非负索引rowIndex 返回该行的值

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
// 总行数
        for(int i = 0; i < rowIndex + 1 ; i++){
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
                    rows.add(result.get(j-1) + result.get(j));
                }
            }
            //把每一行rows的结果添加进最终结果中
            result = rows;
        }
```

#### 最终代码

```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        // 创建result数组存储最终结果
        List<Integer> result = new ArrayList<>();
        
        // 总行数
        for(int i = 0; i < rowIndex + 1 ; i++){
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
                    rows.add(result.get(j-1) + result.get(j));
                }
            }
            //把每一行rows的结果添加进最终结果中
            result = rows;
        }
        
        return result;
    }
}
```

