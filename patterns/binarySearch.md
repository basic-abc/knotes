### Applications
- When given a sorted array, always think of how binary search can be applied
- A division of the valid and invalid values at the optimal value also hints binary search as a viable method

#### Target
- Most of the time, binary search is used to find the insertion point; there are other possibilities however
- It can be applied to find the subarray/window of length k closest to target in a sorted list by comparing the left bound & right bound (as they cannot both be included in the answer), `Math.abs(target - arr[mid + k]) < Math.abs(target - arr[mid])` in [Approach 4 of 272. Closest Binary Search Tree Value II
](https://leetcode.com/problems/closest-binary-search-tree-value-ii/editorial/?envType=study-plan-v2&envId=premium-algo-100)

### Template
```
int l = start
int r = end

while (l < r) { // this ensures while loop always exits on l == r
  int mid = l + (r - l) / 2; // (1) because this favors the left value

  if (target > arr[mid]) { // (3) And this is the condition that makes sense with the increment
    l = mid + 1; // (2) You always want to be incrementing the left value
  } else {
    r = mid;
  }
}
return arr[l] == target ? l : -1;
```

#### mid
- l + (r - l) / 2 favors the left value, or the minimal viable value; this must be accompanied by l = mid + 1, r = mid
- l + (r - l + 1) / 2 favors the right value, or the maximum viable value; this must be accompanied by r = mid - 1, l = mid