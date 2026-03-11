 # Substring with Concatenation of All Words
### Leetcode Hard Challenge

Below are my completed solutions to python challenges on [leetcode](https://leetcode.com/). This page is one of my portfolios in working on python challenges from leetcode.


### 30. Substring with Concatenation of All Words

* **Description:** find whether all consecutive words of a list are present in a string.
* **Links:** [Problem Link](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)


### Approach

#### Initial Approach: Pre-generating Combinations

In the first attempt, the strategy was to pre-calculate every possible combination of words from the list. The idea was to create a "master list" so that the next step would simply involve checking if a substring existed within that list.

*    The Problem: This approach led to massive time and memory overhead.

*    The Scale: Since the word list can contain up to 10,000 elements, the number of potential combinations grows exponentially. This makes it computationally expensive and impractical for standard memory limits.

#### Optimized Approach: Incremental Substring Matching

To solve the efficiency issue, the strategy shifted to a more dynamic "sliding" or "incremental" check. Instead of building combinations upfront, the logic now processes the string piece by piece.
How it works:

*    Extract a Substring: Take a segment of the string and check if it exists in the word list.

*    Recursive Verification: If a match is found, the process moves forward to check the next segment of the string.

*    Success Condition: If the entire string is consumed by matching words from the list, a valid combination is confirmed.

*    Backtracking/Shifting: If a segment does not match or leads to a dead end, the algorithm "shifts" or tries a different segment length to find a valid path.

Key Benefit: This method is significantly more memory-efficient because it only processes what is necessary for the specific input string, rather than trying to map out every mathematical possibility in advance.

### Python Code
```
class Solution:
    def findSubstring(self, s: str, words: List[str]) -> List[int]:
        # print("s",s)


        tot = []
        pjg = len(words[0])
        jml = len(words)

        if (len(list(set(words))) <= 1):
            ww = "".join(words)
            w = 0
            while w < len(s):
                n = s.find(ww,w)
                if (n != -1):
                    tot.append(n)
                    w = n
                w += 1

        else:
            i = 0
            while i < len(s)-pjg+1:
                ck = s[i:i+pjg]
                # print("ck",ck)

                if ck in words:
                    # print("ada nih", ck)

                    wche = words.copy()

                    ke = wche.index(ck)
                    del wche[ke]
                    # print("wc", wche)

                    terus = True
                    j = i + pjg
                    while terus and (wche != []):
                        ge = s[j:j+pjg]
                        # print("ge",ge)
                        if ge not in wche:
                            terus = False
                            # print("gagal")
                        else:
                            ke = wche.index(ge)
                            del wche[ke]
                            # print("wc", wche)

                        j += pjg

                    if wche == []:
                        tot.append(i)
                        # print("yes...")

                i += 1

        tot.sort()
        # print(tot)
        return(tot)

```

* [My LinkedIn Link](https://id.linkedin.com/in/eriyawan) | [My Profile on HackerRank](https://www.hackerrank.com/profile/erimilis) | [My Profile on Leetcode](https://leetcode.com/u/erimilis)

* [My Upwork Profile](https://upwork.com/freelancers/eriyawane) | [My Freelancer Profile](https://www.freelancer.com/u/erimilis)
