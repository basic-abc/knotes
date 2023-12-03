### Properties
- (a + b) % MOD = (a % MOD + b % MOD) % MOD
- (a * b) % MOD = (a % MOD * b % MOD) % MOD
- (a - b) % MOD = (a % MOD - b % MOD + MOD) % MOD
- (a / b) % MOD = a * b ^ (MOD - 2) % MOD
  - Fermat's little Theorem
  - Calculating the inverse with mod is (n ^ (MOD - 2)) % MOD
- Math.floorMod(n, MOD) will always return positive number

### Pointers
- Apply every iteration
- For subtraction, add MOD before final modulo

### Misc
- Python integers can grow arbitrarily large; overflow occurs more commonly in Java and C++

### Templates
- Multiplication with long
```
private int multiply(int a, int b) {
    return (int) ((1L * a * b) % MOD);
}
```
- Inverse modular exponentiation
```
private int inverse(int n) {
    return modExp(n, MOD - 2);
}

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