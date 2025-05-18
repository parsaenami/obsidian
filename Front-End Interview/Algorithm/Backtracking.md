**Idea**: Try all possibilities recursively, backtrack if a path fails.

**Use Cases**:
- Permutations
- Sudoku
- Subsets / combinations

**Example**:
```js
function permute(nums) {
  const result = [];
  function backtrack(path, remaining) {
    if (!remaining.length) return result.push(path);
    for (let i = 0; i < remaining.length; i++) {
      backtrack(path + remaining[i], remaining.slice(0, i).concat(remaining.slice(i + 1)));
    }
  }
  backtrack("", nums);
  return result;
}
```
