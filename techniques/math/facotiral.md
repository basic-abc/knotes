### Factorial
```
private int[] prepareFactorial(int n) {
    int[] fac = new int[n + 1];
    fac[0] = 1;
    for (int i = 1; i <= n; i++) {
        fac[i] = multiply(fac[i - 1], i);
    }
    return fac;        
}
```