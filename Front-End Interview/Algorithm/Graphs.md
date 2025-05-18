**Idea**: Use nodes and edges to model relationships.

**Use Cases**:
- Shortest path
- Cycles detection
- Networks / Trees

**Basic Representations**:
- Adjacency list: `{ A: [B, C], B: [D], ... }`
- Matrix: `graph[i][j] = 1` if edge exists

**Example**:
```js
// BFS
const queue = [start];
const visited = new Set();
while (queue.length) {
  const node = queue.shift();
  if (visited.has(node)) continue;
  visited.add(node);
  for (let neighbor of graph[node]) {
    queue.push(neighbor);
  }
}
```
