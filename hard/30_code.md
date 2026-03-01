# 🚀 LeetCode Solution: Substring with Concatenation of All Words

| Problem ID | Difficulty | Language | Category |
| :--- | :--- | :--- | :--- |
| 30 | <span style="color:red">**Hard**</span> | `Python 3` | `Sliding Window`, `Hash Table` |

---

## 📝 Problem Description
You are given a string `s` and an array of strings `words`. All the strings in `words` are of the **same length**.

A **concatenated substring** in `s` is a substring that contains all the strings of any permutation of `words` concatenated.
* Return the starting indices of all such concatenated substrings.
* The solution must be efficient enough to handle large strings and multiple word repetitions.

> **Example:** > `s = "barfoothefoobarman"`, `words = ["foo","bar"]`  
> **Output:** `[0, 9]`  
> *Explanation: Substrings starting at index 0 and 9 are "barfoo" and "foobar" respectively.*

---

## 💡 Solution Approach: Optimized Sliding Window
Instead of a naive brute-force approach, I implemented an **Optimized Sliding Window** technique to ensure linear time complexity.

### 1. Frequency Mapping
First, I use a `Counter` (Hash Map) to store the required frequency of each word in the `words` array.

### 2. Multi-Pass Sliding Window
Since each word has a fixed length $L$, I perform $L$ separate passes. Each pass starts at a different offset (from $0$ to $L-1$) to cover all possible word alignments in the string `s`.

### 3. Two-Pointer Optimization
Inside each pass, I maintain a window using two pointers (`left` and `right`):
* **Expand:** Move `right` and add the word to a temporary frequency map.
* **Shrink:** If a word frequency exceeds the required count or an invalid word is found, move `left` to shrink the window.
* **Record:** If the number of valid words matches the total count, the `left` index is a valid starting point.

### Complexity Analysis
* **Time Complexity:** $O(n \cdot L)$ — Each character is visited a constant number of times.
* **Space Complexity:** $O(m \cdot L)$ — To store the frequency maps for $m$ words.

---

## 💻 Implementation

```python
from collections import Counter

class Solution:
    def findSubstring(self, s: str, words: list[str]) -> list[int]:
        if not s or not words:
            return []
        
        word_len = len(words[0])
        word_count = len(words)
        total_len = word_len * word_count
        word_freq = Counter(words)
        results = []

        # Optimization: iterate through the word length to cover all offsets
        for i in range(word_len):
            left = i
            right = i
            curr_freq = Counter()
            count = 0
            
            while right + word_len <= len(s):
                word = s[right : right + word_len]
                right += word_len
                
                if word in word_freq:
                    curr_freq[word] += 1
                    count += 1
                    
                    # If we have more of 'word' than needed, slide the left pointer
                    while curr_freq[word] > word_freq[word]:
                        left_word = s[left : left + word_len]
                        curr_freq[left_word] -= 1
                        count -= 1
                        left += word_len
                    
                    # Perfect match found
                    if count == word_count:
                        results.append(left)
                else:
                    # Invalid word found, reset the window
                    curr_freq.clear()
                    count = 0
                    left = right
                    
        return results