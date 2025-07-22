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

### Hot100-[104. 二叉树的最大深度](https://leetcode.cn/problems/maximum-depth-of-binary-tree/)

请看[【基础算法精讲 09】](https://leetcode.cn/link/?target=https%3A%2F%2Fwww.bilibili.com%2Fvideo%2FBV1UD4y1Y769%2F)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if root is None:
            return 0
        l_depth=self.maxDepth(root.left)
        r_depth=self.maxDepth(root.right)
        return max(l_depth,r_depth)+1

```

### Hot100-[226. 翻转二叉树](https://leetcode.cn/problems/invert-binary-tree/)

递归调用 invertTree(root.left)，获取到左子树翻转后的结果 left。
递归调用 invertTree(root.right)，获取到右子树翻转后的结果 right。
交换左右儿子，即更新 root.left 为 right，更新 root.right 为 left。
返回 root。
递归边界：如果 root 是空节点，返回空。

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if root is None:
            return None
        l=self.invertTree(root.left)  # 翻转左子树
        r=self.invertTree(root.right)  # 翻转右子树
        root.left=r # 交换左右儿子
        root.right=l
        return root
```

递归调用 invertTree(root.left)，获取到左子树翻转后的结果 left。
递归调用 invertTree(root.right)，获取到右子树翻转后的结果 right。
交换左右儿子，即更新 root.left 为 right，更新 root.right 为 left。
返回 root。
递归边界：如果 root 是空节点，返回空。

### Hot100-[101. 对称二叉树](https://leetcode.cn/problems/symmetric-tree/)

🌳 超通俗解释：判断二叉树是否对称（像照镜子一样）

想象你有一棵二叉树，要判断它是否对称（左右像镜子一样），就像检查一张脸是否左右对称。这段代码用递归的方式实现了这个功能。

🧩 核心思路：成双成对比较

1. **根节点为空** → 空树算对称（返回 `True`）
2. **根节点不空** → 比较左子树和右子树是否互为镜像

👯 镜像比较规则（递归函数 `recur`）：

每次比较两个节点（比如左子树的A节点和右子树的B节点）：

1. **两个都为空** → 对称 ✅
2. **一个空一个不空** → 不对称 ❌
3. **值不相等** → 不对称 ❌
4. **值相等** → 继续递归检查：
   * A的左孩子 vs B的右孩子（外层比较）
   * A的右孩子 vs B的左孩子（内层比较）

🌰 举个栗子（对称树）：

```
        1
       / \
      2   2
     / \ / \
    3  4 4 3
```

 **检查步骤** ：

1. 根节点1不空 → 比较左2和右2
2. 左2和右2值相等 → 比较：
   * 左2的左3 vs 右2的右3 → 相等
   * 左2的右4 vs 右2的左4 → 相等
3. 所有比较通过 → 树对称 ✅

🚫 反例（不对称树）：

```
        1
       / \
      2   2
       \   \
        3   3
```

 **检查步骤** ：

1. 根节点1不空 → 比较左2和右2
2. 左2和右2值相等 → 比较：
   * 左2的右3 vs 右2的左空 → 不对称 ❌

📜 代码逐行解释：

```python
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        def recur(L, R):  # 递归比较两个节点是否镜像对称
            # 两个都为空 → 对称
            if not L and not R: 
                return True  
            # 一个空或值不等 → 不对称
            if not L or not R or L.val != R.val: 
                return False  
            # 继续比较：外层（L左 vs R右）和内层（L右 vs R左）
            return recur(L.left, R.right) and recur(L.right, R.left)

        # 空树对称，否则比较左右子树
        return not root or recur(root.left, root.right)
```

### Hot100-[543. 二叉树的直径](https://leetcode.cn/problems/diameter-of-binary-tree/)

二叉树的 **直径** 是指树中任意两个节点之间最长路径的 **长度** 。这条路径可能经过也可能不经过根节点 `root` 。

两节点之间路径的 **长度** 由它们之间边数表示。

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        self.ans=1 #初始化最大路径节点数（至少为1，单个节点）

        #定义递归函数：计算子树深度，并更新最大路径
        def depth(root):
            if not root:
                return 0 #空节点深度为0
          
            #递归计算左右子树深度
            l=depth(root.left) #左子树深度
            r=depth(root.right) #右子树深度

            #关键：更新最大路径节点数（当前节点作为转折点）

            self.ans= max(self.ans,l+r+1) # L+R+1 是以当前节点为转折点的路径节点数
            #返回当前子树深度（取左右子树最大深度+1）
            return max(l,r)+1

        depth(root) #从根节点开始递归
        return self.ans-1  # 直径 = 最大路径节点数 - 1（因为边数 = 节点数 - 1）
   

```

假设二叉树如下：

```
    1
   / \
  2   3
 / \
4   5
```

* **最长路径** ：节点 `4 → 2 → 1 → 3` 或 `5 → 2 → 1 → 3`（边数 = 3）。
* **计算过程** ：

1. 节点 `4`：左/右深度=0 → 路径节点数=1（`4`）。
2. 节点 `5`：左/右深度=0 → 路径节点数=1（`5`）。
3. 节点 `2`：左深度=1（`4`的深度），右深度=1（`5`的深度）→ 路径节点数=1+1+1=3（`4→2→5`），更新 `ans=3`。
4. 节点 `3`：左/右深度=0 → 路径节点数=1（`3`）。
5. 节点 `1`：左深度=2（`2`的深度），右深度=1（`3`的深度）→ 路径节点数=2+1+1=4（`4→2→1→3`），更新 `ans=4`。

* **最终结果** ：直径 = `4 - 1 = 3`（边数）。

### Hot100-[102. 二叉树的层序遍历](https://leetcode.cn/problems/binary-tree-level-order-traversal/)

```python
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if root is None:  # 如果树是空的
            return []     # 直接返回空列表
      
        cur = [root]      # 当前层节点列表（初始只包含根节点）
        ans = []          # 存储最终结果的二维列表
      
        while cur:        # 只要当前层还有节点就继续循环
            vals = []     # 存储当前层所有节点的值
            nxt = []      # 存储下一层所有节点
          
            # 遍历当前层的每个节点
            for node in cur:
                vals.append(node.val)  # 记录当前节点的值
              
                # 如果有左孩子，加入下一层列表
                if node.left:
                    nxt.append(node.left)
              
                # 如果有右孩子，加入下一层列表
                if node.right:
                    nxt.append(node.right)
          
            # 当前层处理完毕
            cur = nxt      # 下一层变成新的当前层
            ans.append(vals)  # 把当前层的值列表加入结果
      
        return ans  # 返回层序遍历结果
```

#### 队列

1. **队列的妙用** ：

* 使用 `deque`实现**先进先出（FIFO）**
* `popleft()`高效取出最早加入的节点
* `append()`在右侧添加新节点

1. **分层处理的关键** ：

```python
   for _ in range(len(q)):  # 固定当前层的节点数量
```

   这确保每次循环只处理当前层的所有节点

1. **时间复杂度 O(N)** ：每个节点进出队列各一次
2. **空间复杂度 O(N)** ：最宽层的节点数决定队列大

```python

from collections import deque  # 需要导入deque（代码中省略了这行）

class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if root is None:  # 空树检查
            return []     # 直接返回空列表
  
        ans = []          # 存储最终结果的二维列表
        q = deque([root]) # 初始化队列（双端队列），放入根节点
  
        while q:          # 当队列不为空时循环
            vals = []     # 存储当前层的节点值
    
            # 关键：处理当前层的所有节点
            for _ in range(len(q)):  # 当前层的节点数量
                node = q.popleft()   # 从队列左侧取出节点（先进先出）
                vals.append(node.val) # 记录节点值
        
                # 将子节点加入队列（下一层）
                if node.left:
                    q.append(node.left)
                if node.right:
                    q.append(node.right)
    
            ans.append(vals)  # 将当前层的结果加入最终列表
  
        return ans  # 返回层序遍历结果
```
