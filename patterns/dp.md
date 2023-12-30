### ELI5
- Function or array that represents answer for a given state
- Find recurrence relation between n & n-1
- Find base case

### Keywords
- Output the number of ways
- Minimize / maximize based on a set of rules

### Pitfalls
- Memorization must include each parameter in your recursive function to accurately memorize the state - think of using immutable identifiers over mutable structures to enable memorization

### Applications
- Always draw the decision tree for visualization
  - This [editorial](https://leetcode.com/problems/paint-house/editorial/?envType=study-plan-v2&envId=premium-algo-100) has the best visualization that helps us understand the relation between trees & dp as well as why top-down is associated with implicit tree with recursion
- Identify overlapping sub problems

### Tips
- If number of parameters exceeds 4, consider using a HashMap over a table to avoid TLE