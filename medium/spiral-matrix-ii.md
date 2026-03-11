 # Spiral Matrix II
### Leetcode Medium Challenge

Below are my completed solutions to python challenges on [leetcode](https://leetcode.com/). This page is one of my portfolios in working on python challenges from leetcode.


### 59. Spiral Matrix II
* **Description:** Constructing a matrix with values in a spiral order based on a specified size
* **Links:** [Leetcode Problem](https://leetcode.com/problems/spiral-matrix-ii)


### Approach

The algorithm navigates a 2D array by defining and constantly updating boundary constraints.

*    Boundary Variables: Four specific variables are initialized to track the current limits of the traversal: top, bottom, left, and right. These variables represent the "walls" of the remaining unexplored space.

*    Dynamic Shrinking: As each row or column is fully processed, the corresponding boundary variable is incremented or decremented. This action effectively shrinks the searchable area, preventing the traversal from revisiting the same elements.

*    Directional Control: A dedicated state variable (or a simple integer flag) dictates the current direction of movement—typically starting with right, then moving to down, left, and finally up.

*    Directional Switching: Upon hitting a boundary variable, the direction is immediately updated to the next orientation in the sequence. For example, once the "right" boundary is reached, the top boundary is shifted downward, and the movement direction changes to "down."


### Python Code
```
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        rslt = [[0 for _ in range(n)] for _ in range(n)]

        x = 0  # pointer x
        nx = n # max x
        mx = 0 # min x
        y = 0 # pointer y
        ny = n # max y
        my = 0 # min y
        i = 1 # filler
        arw = ">" # working step arrow
        go = True # while not finish
        while go:
            # print(i, arw, x, y, "mx", mx, "nx", nx, "my", my, "ny", ny)
            rslt[x][y] = i
            i += 1
            if arw == ">":
                y += 1
                if y >= ny:
                    x += 1
                    y -= 1
                    arw = "v"
                    ny = y
                    mx = x
            elif arw == "v":
                x += 1
                if x >= nx:
                    y -= 1
                    x -= 1
                    arw = "<"
                    nx = x
            elif arw == "<":
                y -= 1
                if y < my:
                    x -= 1
                    y += 1
                    arw = "^"
                    my = y +1
            elif arw == "^":
                x -= 1
                if x < mx:
                    y += 1
                    x += 1
                    arw = ">"
                    mx = x + 1
            if ((mx == nx) & (my == ny)) | (x > n) | (y > n) | (i > (n*n)):
                go = False
            # go = False
        # print(rslt)
        return(rslt)

```

* [My LinkedIn Link](https://id.linkedin.com/in/eriyawan) | [My Profile on HackerRank](https://www.hackerrank.com/profile/erimilis) | [My Profile on Leetcode](https://leetcode.com/u/erimilis)

* [My Upwork Profile](https://upwork.com/freelancers/eriyawane) | [My Freelancer Profile](https://www.freelancer.com/u/erimilis)

