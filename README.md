
# Sliding Window

### Max Consecutive ones - https://leetcode.com/problems/max-consecutive-ones-iii/
- This solution you are using sliding window. 
```python
class Solution:
    def longestOnes(self, nums: list[int], k: int) -> int:
        n = len(nums)
        start = 0
        mxm = 0
        count_0 = 0
        one_ind = -1
        for i in range(n):
            if nums[i]==0:
                while(count_0 == k):
                    if nums[start] == 0:
                        count_0-=1
                    start+=1
                else:
                    count_0+=1
                
            mxm = max(i-start+1, mxm)
        return mxm
```

##### Better Solution
- In this solution, you keep the window size fixed, you don't purge it and keep moving forward, we just need the max window size.
```python
class Solution:
    def longestOnes(self, nums: list[int], k: int) -> int:
        left, i = 0,0 
        zeros = 0
        for i in range(len(nums)):
            if nums[i] == 0:
                zeros += 1
            if zeros > k:
                if nums[left] == 0:
                    zeros -= 1
                left += 1
        return len(nums)-left
```

