 # Container With Most Water
### Leetcode Medium Challenge

Below are my completed solutions to python challenges on [leetcode](https://leetcode.com/). This page is one of my portfolios in working on python challenges from leetcode.


### 11. Container With Most Water
* **Description:** Find maximal water in container with candle bar as boundary wall.
* **Links:** [Leetcode Problem](https://leetcode.com/problems/container-with-most-water/)


### Approach

#### The Two-Pointer Approach for Maximum Water Volume

The algorithm determines the maximum area of water that can be contained between two vertical lines (candle bars) by narrowing the search space efficiently.

*    Initial State: The process begins by placing two pointers at the boundaries: a left pointer at the first element and a right pointer at the last element. The initial water volume is calculated by multiplying the distance between the two pointers (width) by the height of the shorter candle bar.

*    Pointer Logic (Left): If the height at the left pointer is less than the height at the right, the left pointer shifts inward to the next candle bar that has a greater height.

*    Pointer Logic (Right): Conversely, if the height at the right pointer is less than or equal to the left, the right pointer shifts to the left until it finds a candle bar with a greater height.

*    Volume Update: After each shift, the new volume is calculated. If this value exceeds the previously recorded maximum volume, it is saved as the new maximum.

*    Termination: This cycle continues until the left and right pointers meet. The highest volume recorded during this process serves as the final solution to the problem.


### Python Code
```

class Solution:
    def maxArea(self, height: List[int]) -> int:
        #print("panjang", len(height))
        xlft = 0
        lft = 0
        xrgt = len(height)-1
        rgt = xrgt
        mx = 0

        while lft < rgt:
            if height[lft] > height[rgt]:
                lev = height[rgt]
            else:
                lev = height[lft]
            lgt = (rgt-lft) * lev
            if lgt > mx:
                mx = lgt

            if height[lft] < height[rgt]:
                lft += 1
            else:
                rgt -= 1

        return mx

```

* [My LinkedIn Link](https://id.linkedin.com/in/eriyawan) | [My Profile on HackerRank](https://www.hackerrank.com/profile/erimilis) | [My Profile on Leetcode](https://leetcode.com/u/erimilis)

* [My Upwork Profile](https://upwork.com/freelancers/eriyawane) | [My Freelancer Profile](https://www.freelancer.com/u/erimilis)
