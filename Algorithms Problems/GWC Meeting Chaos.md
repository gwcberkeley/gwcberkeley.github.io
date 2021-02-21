---
title: Climb the Stairs
parent: Algorithm Problems
grand_parent: Fun Interview Problems
has_children: false
nav_order: 1
---

# Climb the Stairs

You are climbing a staircase. It takes n steps to reach the top. 
Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

```
Example 1:
Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```
```
Example 2:
Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```



<details open markdown="block">
  <summary>
    Approach 1: brute force
  </summary>
  
  If we use brute force, we take all possible step combinations i.e. 1 and 2, at every step. At every step we are calling the function climbStairs for step 1 and 2, and return the sum of returned values of both functions.
  `climbStairs(i,n)=(i + 1, n) + climbStairs(i + 2, n)` 
  where i defines the current step and n defines the destination step.

Code with Java:
```java
public class Solution {
  public int climbStairs(int n) {
      return climb_Stairs(0, n);
  }
  public int climb_Stairs(int i, int n) {
      if (i > n) {
          return 0;
      }
      if (i == n) {
          return 1;
      }
      return climb_Stairs(i + 1, n) + climb_Stairs(i + 2, n);
  }
}
```
  ```
  Time complexity : O(2^n). Size of recursion tree will be 2^n.
  Space complexity : O(n) The depth of the recursion tree can go upto n.
  ```

</details>


<details open markdown="block">
  <summary>
    Approach 2: dynamic programming
  </summary>
  
  We can use dynamic programming here.
  As we can see this problem can be broken into subproblems, and it contains the optimal substructure property i.e. its optimal solution can be constructed efficiently from optimal solutions of its subproblems, we can use dynamic programming to solve this problem.
  One can reach ith step in one of the two ways:
  1. Taking a single step from (i−1)th step.
  2. Taking a step of 2 from (i−2)th step.
  So, the total number of ways to reach ith is equal to the sum of ways of reaching (i−1)th step and ways of reaching (i−2)th step. 

  Let dp[i] denotes the number of ways to reach on ith step:
  `dp[i]=dp[i-1]+dp[i-2]`
  `dp[i]=dp[i−1]+dp[i−2]`


  Code with Java:
  ```java
  public class Solution {
    public int climbStairs(int n) {
        if (n == 1) {
            return 1;
        }
        int[] dp = new int[n + 1];
        dp[1] = 1;
        dp[2] = 2;
        for (int i = 3; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        return dp[n];
    }
  }
  ```
  ```
  Time complexity : O(n). Single loop upto n.
  Space complexity : O(n). dp array of size n is used.
  ```

</details>



<details open markdown="block">
  <summary>
    Approach 3: Fibonacci
  </summary>
  
  As you can see above, the dp array follows a fibonacci sequence. So we can use the definition of fibonacci -- `Fib(n)=Fib(n−1)+Fib(n−2)` or fibonacci formula to calculate the nth fibonacci number. This can help us save the space complexity to O(1). Using matrix multiplication to obtain the nth Fibonacci Number, we can save the time complexity to O(logn).

</details>
