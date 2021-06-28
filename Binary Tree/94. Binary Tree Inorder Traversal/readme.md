## 94. Binary Tree Inorder Traversal

#### 中文题目链接[94. 二叉树的中序遍历](https://leetcode-cn.com/problems/binary-tree-inorder-traversal/)

#### 英文题目链接[94. Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)

- Given the `root` of a binary tree, return *the inorder traversal of its nodes' values*.

   

  **Example 1:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grym6m7ua5j305m090dfs.jpg)

  ```
  Input: root = [1,null,2,3]
  Output: [1,3,2]
  ```

  **Example 2:**

  ```
  Input: root = []
  Output: []
  ```

  **Example 3:**

  ```
  Input: root = [1]
  Output: [1]
  ```

  **Example 4:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grym6kq7cyj305m05ma9x.jpg)

  ```
  Input: root = [1,2]
  Output: [2,1]
  ```

  **Example 5:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grym6j9fw3j305m05mglh.jpg)

  ```
  Input: root = [1,null,2]
  Output: [1,2]
  ```

   

  **Constraints:**

  - The number of nodes in the tree is in the range `[0, 100]`.
  - `-100 <= Node.val <= 100`

   

  **Follow up:** Recursive solution is trivial, could you do it iteratively?

---

## 解题思路

---

### 使用方法：遍历+DFS

---

###题目关键信息

给定一个二叉树的根节点 `root` ，返回它的 **中序** 遍历

---

### 解题步骤

- 中序遍历：左 - 打印 - 右

- 题目要求的是中序遍历，那就按照 左-打印-右这种顺序遍历树就可以了，递归函数实现

  终止条件：当前节点为空时
  函数内：递归的调用左节点，打印当前节点，再递归调用右节点
  时间复杂度：O(n)O(n)
  空间复杂度：O(h)O(h)，hh 是树的高度

---

### 图解

![image.png](https://tva1.sinaimg.cn/large/008i3skNgy1grymgrk0w6j30bm05mq42.jpg)

---

### 代码实现

#### DFS

```java
    void dfs(List<Integer> res, TreeNode root){
        if(root == null){
            return;
        }
        // 打印顺序 左 中 右    
        dfs(res, root.left);
        res.add(root.val);
        dfs(res, root.right);  
```

#### 最终代码

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<Integer>();
        dfs(res, root);
        return res;
        }
    
    void dfs(List<Integer> res, TreeNode root){
        if(root == null){
            return;
        }
        // 打印顺序 左 中 右    
        dfs(res, root.left);
        res.add(root.val);
        dfs(res, root.right);        
        
    }
}
```

