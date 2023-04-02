# 1466. Reorder Routes to Make All Paths Lead to the City Zero

There are `n` cities numbered from `0` to `n - 1` and `n - 1` roads such that there is only one way to travel between two different cities (this network form a tree). Last year, The ministry of transport decided to orient the roads in one direction because they are too narrow.

Roads are represented by `connections` where `connections[i] = [ai, bi]` represents a road from city `ai` to city `bi`.

This year, there will be a big event in the capital (city `0`), and many people want to travel to this city.

Your task consists of reorienting some roads such that each city can visit the city `0`. Return the **minimum** number of edges changed.

It's **guaranteed** that each city can reach city `0` after reorder.

**Example 1:**

<img src="https://assets.leetcode.com/uploads/2020/05/13/sample_1_1819.png" alt="img" style="height: 200px; width: 400px;"/>

```
Input: n = 6, connections = [[0,1],[1,3],[2,3],[4,0],[4,5]]
Output: 3
Explanation: Change the direction of edges show in red such that each node can reach the node 0 (capital).
```
**Example 2:**

<img src="https://assets.leetcode.com/uploads/2020/05/13/sample_2_1819.png" alt="img" style="height: 150px; width: 500px;"/>

```
Input: n = 5, connections = [[1,0],[1,2],[3,2],[3,4]]
Output: 2
Explanation: Change the direction of edges show in red such that each node can reach the node 0 (capital).
```
**Example 3:**
```
Input: n = 3, connections = [[1,0],[2,0]]
Output: 0
``` 

**Constraints:**

* `2 <= n <= 5 * 104`
* `connections.length == n - 1`
* `connections[i].length == 2`
* `0 <= ai, bi <= n - 1`
* `ai != bi`

**Solution:**
```
class Solution {
  public int minReorder(int n, int[][] connections) {
    List<Integer>[] graph = new List[n];

    for (int i = 0; i < n; ++i)
      graph[i] = new ArrayList<>();

    for (int[] conn : connections) {
      graph[conn[0]].add(conn[1]);
      graph[conn[1]].add(-conn[0]); // - := conn[0] -> conn[1]
    }

    return dfs(graph, 0, -1);
  }

  private int dfs(List<Integer>[] graph, int u, int parent) {
    int change = 0;

    for (final int v : graph[u]) {
      if (Math.abs(v) == parent)
        continue;
      if (v > 0)
        ++change;
      change += dfs(graph, Math.abs(v), u);
    }

    return change;
  }
}
```
