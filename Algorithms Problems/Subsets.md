---
title: Subsets
parent: Algorithm Problems
grand_parent: Fun Interview Problems
has_children: false
nav_order: 1
---

# Subsets
(from LeetCode)


Given an integer array nums of unique elements, return all possible subsets (the power set). 
The solution set must not contain duplicate subsets. Return the solution in any order.

```
Example 1:
Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
```
```
Example 2:
Input: nums = [0]
Output: [[],[0]]
```

Constraints:
  - 1<= nums.length <= 10
  - -10 <= nums[i] <= 10
  - All the numbers of nums are unique.



<details>
  <summary>
    Approach 1: Cascading
  </summary>
  
  A straightforward way to think of this question is that we can start from an empty subset in the output list. At each step, we take a new integer into consideration and generate new subsets from the existing ones.

  `For the list [1, 2, 3], we start from {[]} → {[], [1]} → {[], [1], [2], [1, 2]} → etc.`


  ```
    Time complexity : O(N*2^N) to generate all subsets and then copy them into an output list.
    Space complexity : O(N*2^N) This is exactly the number of solutions for subsets multiplied by the number N of elements to keep for each subset.
    For a given number, it could be present or absent (i.e. binary choice) in a subset solution. As a result, for N numbers, we would have in total 2^N choices (solutions).
  ```

</details>


<details>
  <summary>
    Approach 2: Backtracking
  </summary>
  
  ```
    Note: Backtracking is an algorithm for finding all solutions by exploring all potential candidates. If the solution candidate turns out to be not a solution (or at least not the last one), the backtracking algorithm discards it by making some changes on the previous step, i.e. backtracks and then tries again.
  ```
  We can loop over the length of combination, rather than the candidate numbers, and generate all combinations for a given length with the help of backtracking technique.
  We define a backtrack function named `backtrack(first, curr)` which takes the index of the first element to add and a current combination as arguments.
  If the current combination is done, we add the combination to the final output.
  Otherwise, we iterate over the indexes `i` from `first` to the length of the entire sequence `n`.
  Add integer `nums[i]` into the current combination `curr`.
  Proceed to add more integers into the combination : `backtrack(i + 1, curr)`.
  Backtrack by removing `nums[i]` from `curr`.


  Code with Python:
```python
  def subsets(self, nums: List[int]) -> List[List[int]]:
        def backtrack(first = 0, curr = []):
            # if the combination is done
            if len(curr) == k:  
                output.append(curr[:])
                return
            for i in range(first, n):
                # add nums[i] into the current combination
                curr.append(nums[i])
                # use next integers to complete the combination
                backtrack(i + 1, curr)
                # backtrack
                curr.pop()
        
        output = []
        n = len(nums)
        for k in range(n + 1):
            backtrack()
        return output
  ```
  ```
  Time complexity:  O(N * 2 ^ N) to generate all subsets and then copy them into an output list.
  Space complexity: O(N). We are using O(N) space to maintain curr, and are modifying curr in-place with backtracking. Note that for space complexity analysis, we do not count space that is only used for the purpose of returning output, so the output array is ignored.
  ```
</details>

