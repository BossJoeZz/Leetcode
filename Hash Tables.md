哈希表涉及leetcode问题：

Easy:
* 1 Two Sum

### 1. Two Sum (Easy)
[https://leetcode-cn.com/problems/two-sum/](https://leetcode-cn.com/problems/two-sum/)
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hashtable = dict()
        for i, num in enumerate(nums):
            if target - num in hashtable:
                return [hashtable[target - num], i]
            hashtable[nums[i]] = i
        return []
