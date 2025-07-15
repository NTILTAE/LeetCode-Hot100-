### 什么是栈？📚

**栈（Stack）** 是一种简单但强大的 **数据结构** ，它遵循 **"后进先出"（Last In, First Out - LIFO）** 的原则。想象一下现实生活中的例子：

🍽️  **盘子堆叠** ：

* 你洗干净的盘子会一个个叠起来
* 最后放上去的盘子（栈顶）总是最先被取用
* 最先放下的盘子（栈底）最后才会被用到

这就是栈的核心特性！

---

### 栈的核心操作 🔧

栈只有两个基本操作（就像叠盘子）：

1. **入栈（Push）** → 把新元素放到栈顶
2. **出栈（Pop）** → 取出栈顶元素

> 还有一个常用操作：**查看栈顶（Peek）** → 看栈顶元素但不取出

---

### 栈的代码示例（Python）🐍

```python
stack = []  # 用列表模拟栈

# 入栈操作（添加元素）
stack.append(1)   # 栈：[1]
stack.append(2)   # 栈：[1, 2]
stack.append(3)   # 栈：[1, 2, 3]

# 出栈操作（移除并返回栈顶元素）
print(stack.pop())  # 输出：3 → 栈变为：[1, 2]
print(stack.pop())  # 输出：2 → 栈变为：[1]
```

---

### 为什么在遍历二叉树时用栈？🌳

在你之前看到的二叉树遍历代码中：

```python
stack = [(WHITE, root)]  # 初始化栈
while stack:
    color, node = stack.pop()  # 出栈
    # ...处理节点...
    if color == WHITE:
        stack.append((WHITE, node.right))  # 入栈
        stack.append((GRAY, node))
        stack.append((WHITE, node.left))
```

栈在这里发挥了关键作用：

1. **代替递归** ：递归本质就是栈操作，用显式栈可以避免递归深度限制
2. **控制访问顺序** ：通过控制入栈顺序（右→根→左），实现中序遍历（左→根→右）
3. **保存状态** ：用颜色标记保存节点的处理状态（是否已访问）

### Hot100-[94. 二叉树的中序遍历](https://leetcode.cn/problems/binary-tree-inorder-traversal/)

**中序遍历的顺序是：左子树 -> 根节点 -> 右子树**

这段代码是用迭代（非递归）的方式实现二叉树的 **中序遍历** （左子树 → 根节点 → 右子树）。它巧妙地用颜色标记法来模拟递归过程，避免使用递归函数调用栈。

#### 核心思路 🧠

1. **用颜色标记节点状态** ：

* **白色（WHITE）** ：未访问的节点（需要继续处理其子节点）
* **灰色（GRAY）** ：已访问的节点（可以直接输出值）

1. **使用栈模拟递归** ：

* 栈中存储 `(颜色, 节点)` 元组
* 通过控制入栈顺序实现中序遍历

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        WHITE, GRAY = 0, 1  # 定义颜色标记：0=未访问，1=已访问
        res = []  # 存储遍历结果
        stack = [(WHITE, root)]  # 初始化栈，根节点标记为未访问
      
        while stack:  # 当栈不为空时循环
            color, node = stack.pop()  # 弹出栈顶元素
            if node is None:
                continue  # 遇到空节点跳过
          
            if color == WHITE:  # 如果是未访问节点
            # 按【右→根→左】的逆序入栈（因为栈是LIFO后进先出）
                stack.append((WHITE, node.right))  # 右子树（未访问）
                stack.append((GRAY, node))         # 当前节点（标记为已访问）
                stack.append((WHITE, node.left))   # 左子树（未访问）
          
            else:  # 如果是已访问节点（灰色）
                res.append(node.val)  # 输出节点值
      
        return res  # 返回遍历结果
```

🌰 举个栗子（二叉树：1是根，2在左，3在右）

```
    1
   / \
  2   3
```

**正确中序顺序：2 → 1 → 3**

 **执行过程** ：

1. 起点：`[(白,1)]`
2. 弹出1（白）→ 记录：`右门3(白) → 1(灰) → 左门2(白)`
   📒 本本变成：`[ (白,3), (灰,1), (白,2) ]`
3. 弹出2（白）→ 记录：`2的右门(空) → 2(灰) → 2的左门(空)`
   📒 本本变成：`[ (白,3), (灰,1), (灰,2) ]`
4. 弹出2（灰）→ 拿宝物 `2` 💎 → 宝物袋 `[2]`
5. 弹出1（灰）→ 拿宝物 `1` 💎 → 宝物袋 `[2,1]`
6. 弹出3（白）→ 记录：`3的右门(空) → 3(灰) → 3的左门(空)`
   📒 本本变成：`[ (灰,3) ]`
7. 弹出3（灰）→ 拿宝物 `3` 💎 → 宝物袋 `[2,1,3]`
