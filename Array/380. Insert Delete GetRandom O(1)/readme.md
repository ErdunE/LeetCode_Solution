## 380. Insert Delete GetRandom O(1)

#### 中文题目链接[380. O(1) 时间插入、删除和获取随机元素](https://leetcode-cn.com/problems/insert-delete-getrandom-o1/)

#### 英文题目链接[380. Insert Delete GetRandom O(1)](https://leetcode.com/problems/insert-delete-getrandom-o1/)

- Implement the `RandomizedSet` class:

  - `RandomizedSet()` Initializes the `RandomizedSet` object.
  - `bool insert(int val)` Inserts an item `val` into the set if not present. Returns `true` if the item was not present, `false` otherwise.
  - `bool remove(int val)` Removes an item `val` from the set if present. Returns `true` if the item was present, `false` otherwise.
  - `int getRandom()` Returns a random element from the current set of elements (it's guaranteed that at least one element exists when this method is called). Each element must have the **same probability** of being returned.

  You must implement the functions of the class such that each function works in **average** `O(1)` time complexity.

   

  **Example 1:**

  ```
  Input
  ["RandomizedSet", "insert", "remove", "insert", "getRandom", "remove", "insert", "getRandom"]
  [[], [1], [2], [2], [], [1], [2], []]
  Output
  [null, true, false, true, 2, true, false, 2]
  
  Explanation
  RandomizedSet randomizedSet = new RandomizedSet();
  randomizedSet.insert(1); // Inserts 1 to the set. Returns true as 1 was inserted successfully.
  randomizedSet.remove(2); // Returns false as 2 does not exist in the set.
  randomizedSet.insert(2); // Inserts 2 to the set, returns true. Set now contains [1,2].
  randomizedSet.getRandom(); // getRandom() should return either 1 or 2 randomly.
  randomizedSet.remove(1); // Removes 1 from the set, returns true. Set now contains [2].
  randomizedSet.insert(2); // 2 was already in the set, so return false.
  randomizedSet.getRandom(); // Since 2 is the only number in the set, getRandom() will always return 2.
  ```

   

  **Constraints:**

  - `-231 <= val <= 231 - 1`
  - At most `2 * ``105` calls will be made to `insert`, `remove`, and `getRandom`.
  - There will be **at least one** element in the data structure when `getRandom` is called.

---

## 解题思路

---

### 使用方法：HashMap,ArrayList

---

###题目关键信息

设计一个支持在平均 时间复杂度 O(1) 下，执行以下操作的数据结构。

insert(val)：当元素 val 不存在时，向集合中插入该项。
remove(val)：元素 val 存在时，从集合中移除该项。
getRandom：随机返回现有集合中的一项。每个元素应该有相同的概率被返回

---

### 解题步骤

**Insert:**

- 添加元素到动态数组。
- 在哈希表中添加值到索引的映射

**remove:**

- 在哈希表中查找要删除元素的索引。
- 将要删除元素与最后一个元素交换。
- 删除最后一个元素。
- 更新哈希表中的对应关系。

**getRandom：**
借助 Python 中的 `random.choice` 和 Java 中 的 `Random` 实现。

---

### 图解

![image-20210613155443415](https://tva1.sinaimg.cn/large/008i3skNgy1grh9s8ju3xj30ex07egm4.jpg)

![image-20210613155453196](https://tva1.sinaimg.cn/large/008i3skNgy1grh9sduixyj30et07vq3n.jpg)

---

### 代码实现

#### Insert

```java
/** Inserts a value to the set. Returns true if the set did not already contain the specified element. */
public boolean insert(int val) {
  if (dict.containsKey(val)) return false;
    
  dict.put(val, list.size());
  list.add(list.size(), val);
  return true;
}
```

**remove**

```java
/** Removes a value from the set. Returns true if the set contained the specified element. */
public boolean remove(int val) {
  if (! dict.containsKey(val)) return false;

  // move the last element to the place idx of the element to delete
  int lastElement = list.get(list.size() - 1);
  int idx = dict.get(val);
  list.set(idx, lastElement);
  dict.put(lastElement, idx);
  // delete the last element
  list.remove(list.size() - 1);
  dict.remove(val);
  return true;
}
```

**getRandom**

```java
/** Get a random element from the set. */
public int getRandom() {
  return list.get(rand.nextInt(list.size()));
}
```



#### 最终代码

```java
class RandomizedSet {
  Map<Integer, Integer> dict;
  List<Integer> list;
  Random rand = new Random();

  /** Initialize your data structure here. */
  public RandomizedSet() {
    dict = new HashMap();
    list = new ArrayList();
  }

  /** Inserts a value to the set. Returns true if the set did not already contain the specified element. */
  public boolean insert(int val) {
    if (dict.containsKey(val)) return false;

    dict.put(val, list.size());
    list.add(list.size(), val);
    return true;
  }

  /** Removes a value from the set. Returns true if the set contained the specified element. */
  public boolean remove(int val) {
    if (! dict.containsKey(val)) return false;

    // move the last element to the place idx of the element to delete
    int lastElement = list.get(list.size() - 1);
    int idx = dict.get(val);
    list.set(idx, lastElement);
    dict.put(lastElement, idx);
    // delete the last element
    list.remove(list.size() - 1);
    dict.remove(val);
    return true;
  }

  /** Get a random element from the set. */
  public int getRandom() {
    return list.get(rand.nextInt(list.size()));
  }
}
```

