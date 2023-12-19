### ELI5
- Explore all paths recursively

### Variants
- Often in dfs you use a visited Set to avoid reprocessing and/or detecting cycles
  - If that does not prove sufficient, consider 3 states; for example [not processed, processing, processed] or [null, false, true]

#### Examples
- Example of cycle detection using 3 states
```
private int dfsCheckCycle(int node, List<List<Integer>> graph, int[] visited) {
    // return -1 if has a cycle
    // return 1 if does not have any cycle

    if (visited[node] != 0) {
        return visited[node];
    }

    // mark as visiting
    visited[node] = -1;

    for (int endNode : graph.get(node)) {
        if (dfsCheckCycle(endNode, graph, visited) == -1) {
            // we meet a cycle!
            return -1;
        }
    }

    // mark as visited
    visited[node] = 1;
    return 1;
}
```