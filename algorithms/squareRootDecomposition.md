### ELI5
- Method to pre-compute an offline query (query whose values are not updated)
    - Take for example, handling multiple queries to calculate the sum of a sub-array within array
- Divide the array into multiple blocks, for a total of sqrt(n) blocks with size of sqrt(n)
- Compute the sum of each block and cache the total value
- When handling a query whose range envelops any number of pre-computed blocks, we can return the result in O(1)

### Complexity
- Time O(sqrt(n))
- Space O(sqrt(n))

### Implementation
```
int n;
vector<int> a (n);

int len = (int) sqrt (n + .0) + 1;
vector<int> b (len);
for (int i=0; i<n; ++i)
    b[i / len] += a[i];

for (;;) {
    int l, r;
    int sum = 0;
    for (int i=l; i<=r; )
        if (i % len == 0 && i + len - 1 <= r) { // check if contains block
            sum += b[i / len];
            i += len;
        }
        else {
            sum += a[i];
            ++i;
        }
}
```