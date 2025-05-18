**Idea**: Last In First Out (LIFO) structure.

**Use Cases**:
- Undo operations
- Valid parentheses
- Depth-first search

**Example**:
```js
// Valid parentheses
const stack = [];
for (let char of str) {
  if (char === '(') stack.push(char);
  else if (char === ')') {
    if (!stack.length) return false;
    stack.pop();
  }
}
return stack.length === 0;
```
