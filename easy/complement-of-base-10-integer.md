 # Add Two Numbers
### Leetcode Easy Challenge

Below are my completed solutions to python challenges on [leetcode](https://leetcode.com/). This page is one of my portfolios in working on python challenges from leetcode.


### 2. Add two numbers
* **Description:** Sum two non-negative integers represented by linked lists with digits stored in reverse order. Return the final total as a new linked list.
* **Links:** [Solution](medium/add-two-numbers) | [Leetcode Problem](https://leetcode.com/problems/add-two-numbers/)


### Approach

1. Integer to Binary Conversion

The first step is transforming the decimal integer into a binary string, using bin statement. 

2. Transformation into a List

Once the binary representation is obtained, the string or numerical sequence is converted into a list format. This allows for individual access to each bit. For example, the binary string "1010" becomes a list of discrete elements: ['1', '0', '1', '0'].

3. Bit Inversion (The NOT Operation)

A traversal through the list is performed to examine each element. During this iteration, a conditional logic is applied to flip the bits:

*    Every 0 is replaced with a 1.

*    Every 1 is replaced with a 0.

4. Binary back to Integer

The final stage involves joining the modified list back into a string and converting it from base-2 (binary) back to base-10 (decimal). Each position n in the binary sequence (starting from the right at index 0) represents a value of 2n. The sum of these values where the bit is 1 results in the new integer.


### Python Code
```


class Solution:
    def bitwiseComplement(self, n: int) -> int:
        b = bin(n)
        print("b",b)
        blst = list(str(b))
        blst = blst[2:] # delete 0b bin prefix
        # print("blst",blst)

        for i,j in enumerate(blst):
            # print("i",i,"j",j)
            if (j == "0"):
                blst[i] = "1"
            else:
                blst[i] = "0"
        # print(blst)
        rslt = "".join(blst)
        # print("rslt",rslt)
        x = int(rslt,2)
        return x



```

* [My LinkedIn Link](https://id.linkedin.com/in/eriyawan) | [My Profile on HackerRank](https://www.hackerrank.com/profile/erimilis) | [My Profile on Leetcode](https://leetcode.com/u/erimilis)

* [My Upwork Profile](https://upwork.com/freelancers/eriyawane) | [My Freelancer Profile](https://www.freelancer.com/u/erimilis)
