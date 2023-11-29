### Properties
- (a + b) % MOD = (a % MOD + b % MOD) % MOD
- (a * b) % MOD = (a % MOD * b % MOD) % MOD
- (a - b) % MOD = (a % MOD - b % MOD + MOD) % MOD
- Math.floorMod(n, MOD) will always return positive number

### Pointers
- Apply every iteration
- For subtraction, add MOD before final modulo

### Misc
- (a / b) % MOD = a * b ^ (MOD - 2) % MOD
- Python integers can grow arbitrarily large; overflow occurs more commonly in Java and C++