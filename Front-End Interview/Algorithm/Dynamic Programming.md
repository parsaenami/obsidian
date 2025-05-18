**Idea**: Solve complex problems by breaking them down into simpler overlapping subproblems and storing results.

**Use Cases**:
- Fibonacci
- Knapsack
- Longest common subsequence

**Example**:
```js
// Fibonacci with memoization
const fib = (n, memo = {}) => {
  if (n <= 1) return n;
  if (memo[n]) return memo[n];
  return memo[n] = fib(n - 1, memo) + fib(n - 2, memo);
};
```
