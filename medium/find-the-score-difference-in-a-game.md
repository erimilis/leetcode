 # Find The Score Difference In A Game
### Leetcode Medium Challenge

Below are my completed solutions to python challenges on [leetcode](https://leetcode.com/). This page is one of my portfolios in working on python challenges from leetcode.


### 3847. Find The Score Difference In A Game
* **Description:** Find the score difference in a game, between two players in a list.
* **Links:** [Leetcode Problem](https://leetcode.com/problems/find-the-score-difference-in-a-game)


### Approach

The algorithm calculates the score difference between two teams based on a sequential list of values. The distribution follows these specific rules:

*    Initial Ownership: The first value in the list is automatically assigned to the first team.

*    Possession Swapping: Ownership of the current score shifts to the opposing team under two specific conditions:

     *     The value of the element is an odd number.

     *     The element is the 6th item in the sequence (or any multiple of 6).

*    The Overlap Challenge: A unique complexity arises when both conditions are met simultaneously (e.g., the 6th element is also an odd number). In this scenario, the two swap triggers effectively cancel each other out, and the score remains with the previous team.

*    Final Calculation: Once the list is exhausted, the total scores for each team are compared to determine the final point differential.

### Python Code
```

class Solution:
    def scoreDifference(self, nums: List[int]) -> int:
        scr = [0, 0] # score of each player
        ply = 0 # first player
        
        for i in range(len(nums)):
            # print(i, nums[i])
            if (nums[i] % 2 == 1): # swap because odd number
                ply = (ply+1) % 2
                # print("swap", i, ply)
            if ((i+1) % 6 == 0): # swap because 6x
                ply = (ply+1) % 2
                # print("swap", i, ply)
            scr[ply] += nums[i]
            # print(scr)
            
        fnl = scr[0] - scr[1]
        return fnl

```

* [My LinkedIn Link](https://id.linkedin.com/in/eriyawan) | [My Profile on HackerRank](https://www.hackerrank.com/profile/erimilis) | [My Profile on Leetcode](https://leetcode.com/u/erimilis)

* [My Upwork Profile](https://upwork.com/freelancers/eriyawane) | [My Freelancer Profile](https://www.freelancer.com/u/erimilis)

