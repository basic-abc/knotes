### Traversal
- Use traversal work
- Whether substring or subsequence, both avail from one key insight: the recurrence relation is always about referencing the inner palindrome

### Template
- DP traversal; start from the end of the string & reference the sub problems already solved "within" the range
```
int n = s.length();
boolean[][] dp = new boolean[n][n];

int start = 0;
int end = 0;
for (int l = s.length() - 1; l >= 0; l--) {
    for (int r = l + 1; r < s.length(); r++) {
        if (s.charAt(l) == s.charAt(r)) {
            dp[l][r] = dp[l + 1][r - 1] || (r - l <= 2); // r - l <= 2 is for base case; consider s.length() == 2 and s.length() == 3
        } else {
            dp[l][r] = false;
        }
        if (dp[l][r] && (r - l + 1 > end - start + 1)) {
            start = l;
            end = r;
        }
    }
}
```
- Expanding from center is also DP, but is also more straightforward
  - Use an outer loop to consider odd/even centers w/ a helper function that will take O(n)
```
public String longestPalindrome(String s) {
    int start = 0;
    int end = 0;
    for (int i = 0; i < s.length(); i++) {
        int[] odd = expand(i, i, s);
        if (odd[0] > end - start + 1) {
            start = odd[1];
            end = odd[2];
        }

        int[] even = expand(i, i + 1, s);
        if (even[0] > end - start + 1) {
            start = even[1];
            end = even[2];
        }
    }
    return s.substring(start, end + 1);
}
private int[] expand(int l, int r, String s) {
    while (l >= 0 && r < s.length() && s.charAt(l) == s.charAt(r)) {
        l--; r++;
    }
    l++; r--;
    return new int[] { r - l + 1, l, r };
}
```

#### Variants
- DP - minimum insertions needed to make the string a palindrome
  - Note: below adapted to constraint s.length() % 2 == 0
```
int n = s.length();
int[][] dp = new int[n][n];

for (int l = s.length() - 2; l >= 0; l--) {
    for (int r = l + 1; r < s.length(); r++) {
        if (s.charAt(l) == s.charAt(r)) {
            dp[l][r] = dp[l + 1][r - 1];
        } else {
            dp[l][r] = 1 + Math.min(dp[l + 1][r], dp[l][r - 1]);
        }
    }
}
```
