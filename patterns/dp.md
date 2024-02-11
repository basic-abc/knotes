### ELI5
- Function or array that represents answer for a given state
- Find recurrence relation between n & n-1
- Find base case

### Keywords
- Output the number of ways
- Minimize / maximize based on a set of rules

### Pitfalls
- Memorization must include each parameter in your recursive function to accurately memorize the state - think of using immutable identifiers over mutable structures to enable memorization
- Do not mix a DFS / running total approach with DP; running total approaches rely on specific path, while DP is path independent
  - DFS / running total will pass the accumulative result as an argument to the next function call
  - DP will make the calculations within the current method call

### Tips
- Always draw the decision tree for visualization
  - This [editorial](https://leetcode.com/problems/paint-house/editorial/?envType=study-plan-v2&envId=premium-algo-100) has the best visualization that helps us understand the relation between trees & dp as well as why top-down is associated with implicit tree with recursion
- Identify overlapping sub problems; the returned value should always reflect the subproblem's goal
- If number of parameters exceeds 4, consider using a HashMap over a table to avoid TLE

### Top-down vs Bottom-up
- Bottom-up DP must solve subproblems in a specific order and is not as flexible as top-down
- Bottom-up usually needs to solve every subproblem, which may be more subproblems than that of top-down DP
- Bottom-up iterative is faster than top-down recursive call stack
