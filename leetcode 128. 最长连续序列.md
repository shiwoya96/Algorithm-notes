##### leetcode 128. 最长连续序列

```
leetcode 128. 最长连续序列
给定一个未排序的整数数组 nums ，找出数字连续的最长序列（不要求序列元素在原数组中连续）的长度。

进阶：你可以设计并实现时间复杂度为 O(n) 的解决方案吗？

示例 1：

输入：nums = [100,4,200,1,3,2]
输出：4
解释：最长数字连续序列是 [1, 2, 3, 4]。它的长度为 4。
示例 2：

输入：nums = [0,3,7,2,5,8,4,6,0,1]
输出：9
```

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        dic=dict()
        cur_length=0
        max_length=0
        for num in nums:
            if num not in dic:         #dic的键就是num，值就是列表中连续的个数
                left=dic.get(num-1,0)  #查看num-1是否存在dic中，没有存在left=0
                right=dic.get(num+1,0)
                cur_length=right+left+1 
                if cur_length>max_length:
                    max_length=cur_length
                dic[num]=cur_length      #对键num,num-left,num+right的值进行更新
                dic[num-left]=cur_length
                dic[num+right]=cur_length               
        return max_length
```

