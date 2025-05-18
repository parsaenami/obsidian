**Idea**: Use hash maps (objects in JS) to store and lookup data quickly.

**Use Cases**:
- Counting frequency
- Detecting duplicates
- Constant-time lookup

**Example**:
```js
// First non-repeating character
const map = {};
for (let c of str) map[c] = (map[c] || 0) + 1;
for (let c of str) if (map[c] === 1) return c;
```
