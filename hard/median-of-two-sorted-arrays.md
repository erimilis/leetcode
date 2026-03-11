 # Median of Two Sorted Arrays
### Leetcode Hard Challenge

Below are my completed solutions to python challenges on [leetcode](https://leetcode.com/). This page is one of my portfolios in working on python challenges from leetcode.


### 4. Median of Two Sorted Arrays

* **Description:** Find median of two sorted arrays.
* **Links:** [Problem Link](https://leetcode.com/problems/median-of-two-sorted-arrays/)


### Approach

#### 1. Moving from Merging to Direct Selection

Initially, the intuitive approach was to merge the two arrays into a single sorted list and then find the median. However, since the process of merging naturally passes through the middle point anyway, it is more efficient to locate the median directly without the memory overhead of creating a new combined list.

#### 2. Calculating the Median Position

The core logic involves two main steps regarding the total length:

*    Determine Total Length: First, calculate the sum of the lengths of both lists.

*    Identify Index: Based on the total length, calculate the specific index (or indices) where the median resides. Instead of sorting everything, you simply "count" your way through the arrays until you reach that specific position.

#### 3. Handling Even vs. Odd Lengths

The calculation differs slightly depending on the total number of elements:

*    Odd Total: The median is the single element located at the exact center.

*    Even Total: You must identify the two middle elements and calculate their average to find the median.

#### 4. The Edge Case: Sequential Arrays

A particularly interesting and "tricky" scenario occurs when the two lists are already effectively "in order" relative to each other—specifically when:

*    Both lists have the same length.

*    The first element of the second list is greater than or equal to the last element of the first list.

In this case, the arrays are already sorted if placed back-to-back. The "trick" here is that the median will always be the average of the last element of the first list and the first element of the second list.


### Python Code
```
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        ln1 = len(nums1)
        ln2 = len(nums2)
        print("l1", ln1, "l2", ln2)
        ctr = (ln1+ln2) /2
        md = (ln1+ln2) % 2
        print("ctr",ctr,"md",md)
        
        f1 = 0
        f2 = 0
        nu = 0
        x = 0
        while x < ctr:
            if ((f1 < ln1) & (f2 < ln2)):
                if nums1[f1] < nums2[f2]:
                    nu = nums1[f1]
                    f1 += 1
                else:
                    nu = nums2[f2]
                    f2 += 1
            elif (f1 < ln1):
                nu = nums1[f1]
                f1 += 1
            elif (f2 < ln2):
                nu = nums2[f2]
                f2 += 1
            print("nu",nu)
            x += 1
        if md == 0:
            if ((f1 < ln1) & (f2 < ln2)):
                if nums1[f1] < nums2[f2]:
                    nu2 = nums1[f1]
                    f1 += 1
                else:
                    nu2 = nums2[f2]
                    f2 += 1
            elif (f1 < ln1):
                nu2 = nums1[f1]
                f1 += 1
            elif (f2 < ln2):
                nu2 = nums2[f2]
                f2 += 1
            print("nu2", nu2)
            nu = (nu+nu2) / 2

        return nu

```

* [My LinkedIn Link](https://id.linkedin.com/in/eriyawan) | [My Profile on HackerRank](https://www.hackerrank.com/profile/erimilis) | [My Profile on Leetcode](https://leetcode.com/u/erimilis)

* [My Upwork Profile](https://upwork.com/freelancers/eriyawane) | [My Freelancer Profile](https://www.freelancer.com/u/erimilis)
