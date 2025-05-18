**Idea**: A window (subset of elements) slides across the array to track something (like max sum, frequency, etc.)

**Use Cases**:
- Longest/shortest subarray
- Substrings
- Pattern matching

**Example**:
```js
// Find max sum of subarray size k
let sum = 0, max = 0;
for (let i = 0; i < arr.length; i++) {
  sum += arr[i];
  if (i >= k - 1) {
    max = Math.max(max, sum);
    sum -= arr[i - k + 1];
  }
}
```
