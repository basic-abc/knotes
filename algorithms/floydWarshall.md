### ELI5
- 3 nested loops to iteratively find shortest distance by checking if i -> k -> j distance is less than i -> j

### Pitfalls
- Init with infinite distance

### Applications
- Best for finding the shortest paths between all pairs of vertices in a graph
- Can handle negative edge weights if no negative cycles
- Easier implementation if return is `int[][] dist`

### Complexity
- Time O(n^3)

### Implementation
```
    public static final int INF = Integer.MAX_VALUE / 2; // Use a large value (but avoid integer overflow)

    public static int[][] floydWarshall(int[][] graph, int V) {
        int[][] dist = new int[V][V];

        for (int i = 0; i < dist.length; i++) {
            Arrays.fill(dist[i], Integer.MAX_VALUE);
            dis[i][i] = 0;
        }

        for (int i = 0; i < V; i++) {
            for (int j = 0; j < V; j++) {
                dist[i][j] = graph[i][j];
            }
        }

        for (int k = 0; k < V; k++) {
            for (int i = 0; i < V; i++) {
                for (int j = 0; j < V; j++) {
                    if (dist[i][k] != INF && dist[k][j] != INF && dist[i][k] + dist[k][j] < dist[i][j]) {
                        dist[i][j] = dist[i][k] + dist[k][j];
                    }
                }
            }
        }

        return dist;
    }
```
