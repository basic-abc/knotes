### When is it not sliding window
- When window size is not fixed and answer is dependent on the content of the window, rather than the size of the window

### Applications
- Prefix sums are a go-to for subarray sums. Sliding window techniques are excellent for contiguous subarrays with specific properties (like a sum or length)

#### Substring
- Finding all valid occurrence of a substring is commonly solved with sliding window
- Determine if the window is shrinkable or not (if valid substrings will have a fixed length)
  - If shrinkable, the template may be applied directly
  - If not shrinkable, loop through the valid substring window sizes and apply sliding window to each valid window size

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

#### Examples
- [2953. Count Complete Substrings](https://leetcode.com/problems/count-complete-substrings/description/)
- [930. Binary Subarrays With Sum](https://leetcode.com/problems/binary-subarrays-with-sum/description/?envType=daily-question&envId=2024-03-14)
