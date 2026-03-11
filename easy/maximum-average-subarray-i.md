 # Maximum Average Subarray 
### Leetcode Easy Challenge

Below are my completed solutions to python challenges on [leetcode](https://leetcode.com/). This page is one of my portfolios in working on python challenges from leetcode.


### 643. Maximum Average Subarray I
* **Description:** Find the greatest average value, from subarray in a list.
* **Links:** [Solution](easy/maximum-average-subarray-i.md) | [Leetcode Problem](https://leetcode.com/problems/maximum-average-subarray-i)


### Approach

#### 1. The Initial Substring Approach

The original method involved creating a new substring for every possible window and then calculating the average of its elements. While conceptually simple, this approach is computationally expensive.

As the total number of elements increases, the overhead of repeatedly slicing data and performing redundant additions leads to a significant performance bottleneck. For a dataset of size n and a window of size k, the time complexity reaches O(n⋅k), which is inefficient for large-scale data.

#### 2. The Sliding Window Solution

To resolve these efficiency issues, a Sliding Window technique is implemented. This method maintains a running sum of the current window, eliminating the need to recreate substrings.

The process follows these logic steps:

*    Initialization: The sum of the first k elements is calculated once.

*    Subtraction: The element at the very beginning of the current window (the "outgoing" element) is subtracted from the running sum.

*    Addition: The next element in the sequence (the "incoming" element) is added to the sum.

*    Result: The window "slides" forward by one position. The total number of elements remains constant, but the sum is updated in constant time, O(1), for each step.


### Python Code
```

class Solution:
    def findMaxAverage(self, nums: List[int], k: int) -> float:
        x = sum(nums[:k])
        mx = x/k
        # print("mx",mx)
        for i in range(1,len(nums)-k+1):
            x = x - nums[i-1] + nums[i+k-1]
            mx = max(x/k, mx)
        return mx


```

* [My LinkedIn Link](https://id.linkedin.com/in/eriyawan) | [My Profile on HackerRank](https://www.hackerrank.com/profile/erimilis) | [My Profile on Leetcode](https://leetcode.com/u/erimilis)

* [My Upwork Profile](https://upwork.com/freelancers/eriyawane) | [My Freelancer Profile](https://www.freelancer.com/u/erimilis)
