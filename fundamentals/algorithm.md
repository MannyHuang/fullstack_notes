# Algorithm

## 五大算法

- 贪心算法: 局部最优解法
- 分治算法: 分成多个小模块，与原问题性质相同
- 动态规划: 每个状态都是过去历史的一个总结
- 回溯法: 发现原先选择不优时，退回重新选择
- 分支限界法

## 基础排序算法

- 冒泡排序: 两两比较
- 选择排序: 遍历自身以后的元素，最小的元素跟自己调换位置
- 插入排序: 即将元素插入到已排序好的数组中

## 高级排序算法

- 快速排序
- 希尔排序：不定步数的插入排序，插入排序
- 稳定性：插冒归基稳定，快选堆希不稳定

## 树

- 二叉树: 最多只有两个子节点
  - 完全二叉树
  - 满二叉树
    - 深度为 k
    - 节点数为 n，
    - n = 2^k - 1

## 二叉树遍历方法

- 宽度优先
  - 队列的数据结构来帮助我们做广度优先搜索
  - 本质是前序遍历

```js
var levelOrder = function(root) {
  let res = [];

  function preOrder(root, level) {
    if (root) {
      if (res[level]) res[level].push(root.val);
      else res[level] = [root.val];
      preOrder(root.left, level + 1);
      preOrder(root.right, level + 1);
    }
  }
  preOrder(root, 0);
  return res;
};
```

- 深度优先
  - 前序遍历：根左右
  - 中序遍历：左根右
  - 后序遍历：左右根

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[]}
 */
var postorderTraversal = function(root) {
  const result = [];

  function func(root, result) {
    if (root == null) return;
    if (root.left) func(root.left, result);
    if (root.right) func(root.right, result);
    result.push(root.val);
  }
  func(root, result);
  return result;
};
```

## 二叉查找树: 是一种特殊的二叉树，能有效地提高查找效率

- 小值在左，大值在右
- 节点 n 的所有左子树值小于 n，所有右子树值大于 n

## 堆

- 大顶堆：根结点为最大值，每个结点的值大于或等于其孩子结点的值。
- 小顶堆：根结点为最小值，每个结点的值小于或等于其孩子结点的值。
- 堆的存储： 堆由数组来实现，相当于对二叉树做层序遍历
- 对于结点 i ，其子结点为 2i+1 与 2i+2
