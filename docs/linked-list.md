### Hot100-[160. 相交链表](https://leetcode.cn/problems/intersection-of-two-linked-lists/)

具体算法如下：

初始化两个指针 p=headA, q=headB。
不断循环，直到 p=q。
每次循环，p 和 q 各向后走一步。具体来说，如果 p 不是空节点，那么更新 p 为 p.next，否则更新 p 为 headB；如果 q 不是空节点，那么更新 q 为 q.next，否则更新 q 为 headA。
循环结束时，如果两条链表相交，那么此时 p 和 q 都在相交的起始节点处，返回 p；如果两条链表不相交，那么 p 和 q 都走到空节点，所以也可以返回 p，即空节点。

```python
classSolution:  
	defgetIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:  
		p,q=headA,headB  
		while p isnot q:
			p=p.next if p else headB    
			q=q.next if q else headA  
		return p
```

### Hot100-[206. 反转链表](https://leetcode.cn/problems/reverse-linked-list/)

**简单理解** ：比如链表为 **1**→**2**→**3**。创建一个新的空链表，然后用**头插法**依次把节点 **1**,**2**,**3** 插到这个新链表的头部，就得到了链表 **3**→**2**→**1**，这正是反转后的链表。

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
	pre=None
	cur=head
	while cur:
		nxt=cur.next
		cur.next=pre
		pre=cur
		cur=nxt
	return pre
```

代码功能

这是一个经典的链表反转算法，使用迭代的方式将单链表反转。

变量说明

* `pre`: 用于存储当前节点的前一个节点，初始为 `None`
* `cur`: 当前正在处理的节点，初始为链表头 `head`
* `nxt`: 临时存储当前节点的下一个节点

算法步骤

1. 初始化 `pre`为 `None`，`cur`为链表头 `head`
2. 进入循环，条件是当前节点 `cur`不为空
3. 在循环中：
   * 先保存当前节点的下一个节点到 `nxt`（因为后面要修改 `cur.next`）
   * 将当前节点的 `next`指针指向前一个节点 `pre`（反转操作）
   * 将 `pre`移动到当前节点 `cur`
   * 将 `cur`移动到之前保存的下一个节点 `nxt`
4. 当 `cur`为 `None`时，循环结束，此时 `pre`就是新链表的头节点

### Hot100-[234. 回文链表](https://leetcode.cn/problems/palindrome-linked-list/)

#### **面试实现简单代码**

时间复杂度O(n)  空间复杂度O(n)

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        vals=[]
	current_node=head
	while current_node is not None:
		vals.append(current_node.val)
		current_node=current_node.next
	return vals==vals[::-1]
```

这段代码实现了一个简单的 **回文链表（Palindrome Linked List）** 检测方法。它的思路是：

1. **遍历链表，把所有节点的值存入一个列表 `vals`** ：

* `current_node = head`：从链表头开始遍历。
* `while current_node is not None:`：循环直到链表末尾。
* `vals.append(current_node.val)`：把当前节点的值加入列表。
* `current_node = current_node.next`：移动到下一个节点。

1. **检查列表 `vals` 是否等于它的逆序 `vals[::-1]`** ：

* `vals[::-1]` 是 Python 的切片操作，表示反转列表。
* 如果 `vals == vals[::-1]`，说明链表的值是回文的（正读反读都一样），返回 `True`，否则返回 `False`。

**示例**

假设链表是 `1 -> 2 -> 2 -> 1`：

* `vals = [1, 2, 2, 1]`
* `vals[::-1] = [1, 2, 2, 1]`
* `vals == vals[::-1]` → `True`（是回文链表）

假设链表是 `1 -> 2 -> 3`：

* `vals = [1, 2, 3]`
* `vals[::-1] = [3, 2, 1]`
* `vals == vals[::-1]` → `False`（不是回文链表）

#### 时间复杂度O(n)  空间复杂度O(1)的解法

step1 查找链表中间节点

step2 反转链表

step3 判断是否为回文链表

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    #876. 链表的中间节点
    def middleNode(self,head: Optional[ListNode])->Optional[ListNode]:
        slow=fast=head #初始化两个指针，都指向头部
        while fast and fast.next: #当快指针开始移动
	        slow=slow.next #慢指针每次移动一步
	        fast=fast.next.next #快指针每次移动两步
        return slow  #快指针到末尾时，慢指针就在中间
    #206. 反转列表
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        pre, cur = None, head
        while cur:
            nxt = cur.next
            cur.next = pre
            pre = cur
            cur = nxt
        return pre

    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        mid = self.middleNode(head)
        head2 = self.reverseList(mid)
        while head2:
            if head.val != head2.val:
                return False
            head = head.next
            head2 = head2.next
        return True
```

### Hot100-[141. 环形链表](https://leetcode.cn/problems/linked-list-cycle/)

类似于龟兔赛跑，设置两个节点，一个一次移动一个节点，一个一次移动两个节点

如果有环的话，那么某个时刻，快的节点会追上慢的节点

```python
class Solution:
    def hasCycle(self,head:Optional[ListNode])->bool:
        slow,fast=head,head #龟兔同时从前出发
        while fast and fast.next:
            slow=slow.next #乌龟先走一步
            fast=fast.next.next #兔子走两步 
            if fast is slow: #兔子追上乌龟，说明有环
                return True
        return False #访问到末尾，说明没环
```
