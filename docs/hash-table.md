## 常见哈希表创建方式

### 普通字典：`d = {}`

Hot100-[1. 两数之和](https://leetcode.cn/problems/two-sum/) 采用这样

先创建一个harsh表，再对i,num遍历nums  i为序号，num为数字

如果complement=目标-num

如果complement在harsh表，返回complement和他在harsh表的位置

### defaultdict：`d = defaultdict(list/int/set)`

Hot100-[49. 字母异位词分组](https://leetcode.cn/problems/group-anagrams/) 采用将list直接转为harsh 

适用于分组、计数等场景，访问不存在的key时会自动创建默认值

首先for 循环遍历strs，sorted(s) 把字符串的s排序，放回一个列表

' '.join() 把排序后的字符列表拼成字符串，比如‘eat’->' aet'

这样异位词排序后都一样，作为harsh表的key

再return list(d.values())  哈希表的 value 保存分组后的结果

### set（哈希集合）

Hot100-[128. 最长连续序列](https://leetcode.cn/problems/longest-consecutive-sequence/) 采用这种

首先ans为1，将nums转为set()，再x遍历harsh表，如果x-1 in harsh continue

一个令y=x+1 while 最后ans=max(ans,y-x)

return ans

最后相减

* Counter：`c = Counter(list)`
* 字典推导式
* dict.fromkeys
* 用不可变类型做key
* 嵌套字典
