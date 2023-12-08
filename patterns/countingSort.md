### ELI5
- Create empty array of size k (value range)
- Count frequency of small integers
- Iterate array for cumulative sum
- Use this aux array as the mapping from original value to new index (account for 0-based index by decrementing 1)
- Update aux array position decrementing by 1 to handle duplicate values
- Obtain new sorted array

### Complexity
- Time O(n + k)
- Space O(k)
k is the size of the range of possible values

### Applications
- Leetcode problems that involve the frequency of small integers may indicate counting sort as a viable solution

### Misc
- Stable sort algorithm (same value will retain relative order)
- Runtime does not degrade, as opposed to O(n^2) for other sort algorithms
- Non-Comparison based - values are not compared for sorting
- Unsuitable for large ranges 
- Applied as subroutine in Radix Sort

### Examples
- [1887. Reduction Operations to Make the Array Elements Equal](https://leetcode.com/problems/reduction-operations-to-make-the-array-elements-equal/)
