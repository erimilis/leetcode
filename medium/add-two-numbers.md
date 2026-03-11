 # Add Two Numbers
### Leetcode Medium Challenge

Below are my completed solutions to python challenges on [leetcode](https://leetcode.com/). This page is one of my portfolios in working on python challenges from leetcode.


### 2. Add two numbers
* **Description:** Sum two non-negative integers represented by linked lists with digits stored in reverse order. Return the final total as a new linked list.
* **Links:** [Solution](medium/add-two-numbers) | [Leetcode Problem](https://leetcode.com/problems/add-two-numbers/)


### Approach

When the digits are stored in reverse order (ones, then tens, then hundreds), we can iterate through both lists simultaneously. We calculate the sum of the values at each corresponding node, just as we would add numbers column by column on paper.
#### The Challenge: Handling the Carry

The primary challenge in this approach is managing the carry.

*    The Threshold: Whenever the sum of two digits (plus any existing carry from the previous step) is 10 or greater, we cannot store the entire value in a single node.

*    The Logic: We must store only the remainder (the last digit) in the current node. The "1" (the carry) must be passed forward to be added to the next pair of nodes.

*    The Final Step: A common edge case occurs at the very end of the lists. If a carry remains after the last two digits are added, a new node must be appended to the result list to hold that final "1".

### Python Code
```

# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        
        new = ListNode(0)
        c = new
        x = 0
        while l1 or l2 or x:
            v1 = l1.val if l1 else 0
            v2 = l2.val if l2 else 0
            # print("v1", v1, "v2", v2)

            t = v1 + v2 + x
            x = t // 10
            n = t % 10
            # print("n",n, "x",x)

            c.next = ListNode(n)
            c = c.next
            if l1: l1 = l1.next
            if l2: l2 = l2.next
        return new.next
        
```

* [My LinkedIn Link](https://id.linkedin.com/in/eriyawan) | [My Profile on HackerRank](https://www.hackerrank.com/profile/erimilis) | [My Profile on Leetcode](https://leetcode.com/u/erimilis)

* [My Upwork Profile](https://upwork.com/freelancers/eriyawane) | [My Freelancer Profile](https://www.freelancer.com/u/erimilis)
