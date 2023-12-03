### (Modular) Exponentiation
```
private int modExp(int base, int exp) {
    int res = 1;
    while (exp > 0) {
        if (exp % 2 == 1) {
            res = multiply(res, base);
        }
        base = multiply(base, base);
        exp /= 2;
    }
    return res;
}
```

### Power of 2
```
private int[] preparePow2(int n) {
    int[] pow2 = new int[n + 1];
    pow2[0] = 1;
    for (int i = 1; i <= n; i++) {
        pow2[i] = multiply(pow2[i - 1], 2);
    }
    return pow2;
}
```