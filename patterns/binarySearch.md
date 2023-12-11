### Applications
- When given a sorted array, always think of how binary search can be applied

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