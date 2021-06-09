## 56. Merge Intervals

#### 中文题目链接[56. 合并区间](https://leetcode-cn.com/problems/merge-intervals/)

#### 英文题目链接[56. Merge Intervals](https://leetcode.com/problems/merge-intervals/)

- Given an array of `intervals` where `intervals[i] = [starti, endi]`, merge all overlapping intervals, and return *an array of the non-overlapping intervals that cover all the intervals in the input*.

   

  **Example 1:**

  ```
  Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
  Output: [[1,6],[8,10],[15,18]]
  Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].
  ```

  **Example 2:**

  ```
  Input: intervals = [[1,4],[4,5]]
  Output: [[1,5]]
  Explanation: Intervals [1,4] and [4,5] are considered overlapping.
  ```

   

  **Constraints:**

  - 1 <= intervals.length <= 10^4^
  - `intervals[i].length == 2`
  - 0 <= start~i~ <= endi <= 10^4^

---

## 解题思路

---

### 使用方法：排序

---

###题目关键信息

一个表示若干个区间的数组 `intervals`

每个区间为 intervals[i] = [start~i~, end~i~]

合并所有重叠的区间，返回不重叠的区间数组

该数组需覆盖输入中的所有区间

---

### 解题步骤

设置返回变量 数组merged

将数组排序，按每一个区间的左端点升序进行排序，即start~i~

将第一个区间加入merged数组中

如果当前区间的左端点在数组中merged中的最后一个区间的右端点之后，那么他们不会重合

将当前区间加入数组merged的末尾

否则，他们重合，我们需要用当前区间的右端点更新数组merged中最后一个区间的右端点

将其更新为 当前区间右端点，和merged中最后一个区间的右端点 中的较大值

循环上述步骤直到最后一组区间

返回merged

----

### 图解

![image-20210609155123468](https://tva1.sinaimg.cn/large/008i3skNgy1grcn7io5ovj30fd03nmxf.jpg)

---

### 代码实现

#### 排序

```java
for(int i=1; i<intervals.length ; i++){
            // 如果当前区间的左端点在数组中merged中的最后一个区间的右端点之后，那么他们不会重合
            if(merged.get(merged.size()-1)[1] < intervals[i][0]){
                // 将当前区间加入数组merged的末尾
                merged.add(intervals[i]);
            }
            // 否则，他们重合，我们需要用当前区间的右端点更新数组merged中最后一个区间的右端点
            else{
                // 将其更新为 当前区间右端点，和merged中最后一个区间的右端点 中的较大值
                merged.get(merged.size()-1)[1] = Math.max(merged.get(merged.size()-1)[1], intervals[i][1]);
            }
            // 循环上述步骤直到最后一组区间
        }  
```

#### 最终代码

```java
class Solution {
    public int[][] merge(int[][] intervals) {
        // 特判
        if(intervals.length == 0 || intervals == null){
            return intervals;
        }
        
        // 设置返回变量 数组merged
        List<int[]> merged = new ArrayList<int[]>();
        
        // 将数组排序，按每一个区间的左端点升序进行排序
        Arrays.sort(intervals, (v1, v2) -> v1[0] - v2[0]);
        
        // 将第一个区间加入merged数组中
        merged.add(intervals[0]);
        
        for(int i=1; i<intervals.length ; i++){
            // 如果当前区间的左端点在数组中merged中的最后一个区间的右端点之后，那么他们不会重合
            if(merged.get(merged.size()-1)[1] < intervals[i][0]){
                // 将当前区间加入数组merged的末尾
                merged.add(intervals[i]);
            }
            // 否则，他们重合，我们需要用当前区间的右端点更新数组merged中最后一个区间的右端点
            else{
                // 将其更新为 当前区间右端点，和merged中最后一个区间的右端点 中的较大值
                merged.get(merged.size()-1)[1] = Math.max(merged.get(merged.size()-1)[1], intervals[i][1]);
            }
            // 循环上述步骤直到最后一组区间
        }  
        // 返回merged
        return merged.toArray(new int[merged.size()][2]);
    }
}
```

