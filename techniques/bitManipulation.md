### Cheat sheet
- shifting n >>= 1
- mask = 1 << i
- n & mask to find bit at mask index

### Signed vs Unsigned
- Java does not have unsigned integers
- Java represents signed integers using [2's complement notation](https://www.interviewcake.com/concept/python/binary-numbers?#twos-complement) (the leftmost digit is negative, while the rest is positive, summing up to the represented integer)

### Arithmetic shift vs Logical right shift
- << left shift - most-significant bit is lost, and a 0-bit is inserted from the right end
- >>> logical right shift - least-significant bit is lost, and a 0-bit is inserted from the left end
- >> arithmetic right shift - least-significant bit is lost, and the most-significant bit is copied

### Misc
- watch when you need long, i.e. long mask = 1L << i
- [n &= (n - 1) always flips the least-significant 1-bit to 0](https://leetcode.com/problems/number-of-1-bits/editorial/?envType=daily-question&envId=2023-11-29)