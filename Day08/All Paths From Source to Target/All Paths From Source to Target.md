# 797. All Paths From Source to Target

Given a directed acyclic graph (DAG) of n nodes labeled from 0 to n - 1, find all possible paths from node 0 to node n - 1 and return them in any order.

The graph is given as follows: graph[i] is a list of all nodes you can visit from node i (i.e., there is a directed edge from node i to node graph[i][j]).

**Example 1:**

![alt-text]
```
Input: graph = [[1,2],[3],[3],[]]
Output: [[0,1,3],[0,2,3]]
Explanation: There are two paths: 0 -> 1 -> 3 and 0 -> 2 -> 3.
```
**Example 2:**
```
Input: graph = [[4,3,1],[3,2,4],[3],[4],[]]
Output: [[0,4],[0,3,4],[0,1,3,4],[0,1,2,3,4],[0,1,4]]
```

**Constraints:**

* ```n == graph.length```
* ```2 <= n <= 15```
* ```0 <= graph[i][j] < n```
* ```graph[i][j] != i``` (i.e., there will be no self-loops).
* All the elements of graph[i] are unique.
* The input graph is guaranteed to be a DAG.

**Solution:**
```
class Solution {
    class Node {
        int vertex;
        List<Integer> list;
        public Node(int v, List<Integer> l) {
            vertex = v;
            list = l;
        }
    }
    
    public List<List<Integer>> allPathsSourceTarget(int[][] graph) {
        int len = graph.length;
        List<List<Integer>> res = new ArrayList<>();
        Queue<Node> queue = new LinkedList<>();
        queue.offer(new Node(0, new ArrayList<Integer>()));
        while (!queue.isEmpty()) {
            Node curr = queue.poll();
            curr.list.add(curr.vertex);
            if (curr.vertex == len - 1) {
                res.add(curr.list);
            } else {
                for (int nextVertex : graph[curr.vertex]) {
                    queue.offer(new Node(nextVertex, new ArrayList<Integer>(curr.list)));
                }
            }
        }
        return res;
    }
}
```
