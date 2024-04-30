### Template
```
public int gcd(int n, int m) {
    int a = Math.max(n, m);
    int b = Math.min(n, m);
    if (b == 0) return a;
    return gcd(b, a % b);
}
```