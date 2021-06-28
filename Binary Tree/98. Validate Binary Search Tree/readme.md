## 98. Validate Binary Search Tree

#### 中文题目链接[98. 验证二叉搜索树](https://leetcode-cn.com/problems/validate-binary-search-tree/)

#### 英文题目链接[98. Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)

- Given the `root` of a binary tree, return *the inorder traversal of its nodes' values*.

   

  **Example 1:**

  ![img](https://tva1.sinaimg.cn/large/008i3skNgy1grym6m7ua5j305m090dfs.jpg)

  ```
  Given the root of a binary tree, determine if it is a valid binary search tree (BST).
  
  A valid BST is defined as follows:
  
  The left subtree of a node contains only nodes with keys less than the node's key.
  The right subtree of a node contains only nodes with keys greater than the node's key.
  Both the left and right subtrees must also be binary search trees.
   
  
  Example 1:
  
  
  Input: root = [2,1,3]
  Output: true
  Example 2:
  
  
  Input: root = [5,1,4,null,null,3,6]
  Output: false
  Explanation: The root node's value is 5 but its right child's value is 4.
   
  
  Constraints:
  
  The number of nodes in the tree is in the range [1, 104].
  -231 <= Node.val <= 231 - 1Input: root = [1,null,2,3]
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

### 使用方法：遍历+中序排列

---

###题目关键信息

给定一个二叉树，判断其是否是一个有效的二叉搜索树

假设一个二叉搜索树具有如下特征：

- 节点的左子树只包含**小于**当前节点的数。
- 节点的右子树只包含**大于**当前节点的数。
- 所有左子树和右子树自身必须也是二叉搜索树。

---

### 解题步骤

- 中序遍历。二叉搜索树中序遍历得到升序，对给定的二叉树中序遍历，结果记录于res之中，检验res是否为严格的升序，若是则为true，反之false

---

### 图解

---

### 代码实现

#### DFS

```java
    // 中序遍历。二叉搜索树中序遍历得到升序，
    private void inOrder(TreeNode root){
        if(root != null){
            inOrder(root.left);
            res.add(root.val);
            inOrder(root.right);
        }
    }
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
    // 对给定的二叉树中序遍历，结果记录于res之中
    List<Integer> res = new ArrayList<>();
    public boolean isValidBST(TreeNode root) {
        if(root == null){
            return true;
        }
        inOrder(root);
        // 检验res是否为严格的升序
        for(int i=1 ; i <res.size() ; i++){
            if(res.get(i) <= res.get(i-1)){
                // 反之false
                return false;
            }
        }
        // 若是则为true
        return true;   
    }
    // 中序遍历。二叉搜索树中序遍历得到升序，
    private void inOrder(TreeNode root){
        if(root != null){
            inOrder(root.left);
            res.add(root.val);
            inOrder(root.right);
        }
    }
}
```

