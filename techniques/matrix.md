### Linear Algebra
- Multiplication basics
```
for (row = 0 to n) {
    for (elementPos = 0 to k) {
        if (mat1[row][elementPos] != 0) {
            for (col = 0 to m) {
                ans[row][col] += mat1[row][elementPos] * mat2[elementPos][col];
            }
        }
    }
}
```
- [Sparse matrix](https://leetcode.com/problems/sparse-matrix-multiplication/editorial/?envType=study-plan-v2&envId=premium-algo-100) creates Row, Col Pairs to 'save space'; or the formal Yale Format (Compressed Sparse Row / Column)