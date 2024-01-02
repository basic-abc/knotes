### Applications
- When your output needs to list all valid permutations

### Tips
- Focus on looking for the recurrence relation & implementing state management

### General Template
```
void backtrack(int start, List<Integer> temp, int n) {
    if (isSolution(temp, n)) {
        storeSolution(temp);
        return;
    }

    for (int i = start; i <= n; i++) {
        if (isValidChoice(i, temp, n)) {
            makeChoice(i, temp);
            backtrack(i + 1, temp, n); // 'i + 1' for next decision
            undoChoice(i, temp); // Backtrack
        }
    }
}
```

#### Examples
- [254. Factor Combinations](https://leetcode.com/problems/factor-combinations/description/?envType=study-plan-v2&envId=premium-algo-100)