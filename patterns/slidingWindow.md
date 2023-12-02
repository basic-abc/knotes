### Templates
- Window is shrinkable
```
int i = 0, j = 0, ans = 0;
while (j < N) {
    // use A[j] to update state which might make the window invalid
    while (invalid()) { // when invalid, repeatedly shrink the window by incrementing left edge until window is valid again
        // update state using A[i]
    }
    ans = max(ans, j - i + 1); // the window [i, j] is the maximum window we've found thus far
    j++;
}
return ans;
```
- Window is non-shrinkable
```
int i = 0, j = 0;
while (j < N) {
    // use A[j] to update state which might make window invalid
    if (invalid()) { // Increment the left edge ONLY when the window is invalid - the window 'grows' when valid, but 'shifts' when it's invalid
        // CODE: update state using A[i]
        ++i;
    }
    j++;
    // after `++j` the window `[i, j)` of length `j - i` might be invalid
}
return j - i; // there must be a maximum window of size `j - i`
```