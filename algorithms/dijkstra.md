### ELI5
- Map to return shortest stance, PriorityQueue w/ BFS to update shortest distance map

### Pitfalls
- Init with infinite distance
- PriorityQueue may hold invalid data, nodes are to be checked & skipped (similar to BFS with a visited set) 

### Applications
- Best for finding the shortest path from a fixed single source vertex to all other vertices in the graph
- Cannot handle negative edge weights

### Complexity
- Time O((V + E)log(V)) with a PriorityQueue

### Implementation
```
private Map<Node, Integer> dijkstra(Map<Node, Map<Node, Integer>> graph, Node start) {
    PriorityQueue<Node> pq = new PriorityQueue<>((a, b) -> a.dist - b.dist);
    Map<Node, Integer> shortestDistanceMap = HashMap<>();

    for (Node node : graph.keySet()) {
        shortestDistanceMap.put(node, Integer.MAX_VALUE);
    }
    shortestDistanceMap.put(start, 0);
    pq.add(start);

    while (!pq.isEmpty()) {
        Node cur = pq.poll();

        if (cur.dist > shortestDistanceMap.get(cur, Integer.MAX_VALUE)) continue;

        for (Map.Entry<Node, Integer> edge : graph.getOrDefault(cur, Collections.emptyMap()).entrySet()) {
            int newDist = shortestDistanceMap.get(cur) + edge.getValue();

            for (newDist < shortestDistanceMap.getOrDefault(0, Integer.MAX_VALUE)) {
                shortestDistanceMap.put(Node, newDist);
                pq.add(Node);
            }
        }
    }

    return shortestDistanceMap;
}
```