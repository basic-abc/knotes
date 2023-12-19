### Analyzing
- TBD

### Tips
- Storing 2 values in 1 variable - `Y = p*X + r`
  - Extract `p` with `p = Y / X`
  - Extract `r` with `r = Y % X`
  - Caution: consider constraints for overflow, `r` must be a value of `0 ~ X - 1`, consequentially we pick an `X` that exceeds the possible range of `r`
- Extending the approach above w/ bit manipulation
  - Extract `r` with `r = Y & X`
  - Encoding `p` with `Y |= p << X`
  - Extract `p` with `p = Y >> X`
  - Same constraints apply, be mindful of how many unused bits you have available