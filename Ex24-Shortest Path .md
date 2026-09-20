# Ex24 Shortest Path and Reachability in a Heritage Town using BFS

## DATE: 20/09/2026

## AIM:

To design and implement a Java program that, given a map of attractions in a heritage town connected by walking paths, recommends:
The shortest number of paths (minimum hops) from a starting attraction to a target attraction.
The number of reachable attractions from the same starting point using Breadth-First Search (BFS).

## Algorithm

1. Read the number of attractions, paths, starting attraction, and target attraction.
2. Create an adjacency list to represent the walking paths between attractions.
3. Use BFS from the starting attraction and maintain a distance array to find the minimum number of hops.
4. Count the number of attractions visited during the BFS traversal.
5. Display the shortest path distance and the total number of reachable attractions.

## Program:

```java id="7x2c1m"
/*
Program to determine Shortest Path and Reachability in a Heritage Town using BFS
Developed by: LAKSHMIDHAR N
RegisterNumber:  212224230138
*/

import java.util.*;

public class Main {

    static void bfs(ArrayList<ArrayList<Integer>> graph, int start,
                    int target, int n) {

        boolean[] visited = new boolean[n];
        int[] distance = new int[n];
        Arrays.fill(distance, -1);

        Queue<Integer> queue = new LinkedList<>();

        visited[start] = true;
        distance[start] = 0;
        queue.add(start);

        int reachable = 0;

        while (!queue.isEmpty()) {
            int current = queue.poll();
            reachable++;

            for (int neighbour : graph.get(current)) {
                if (!visited[neighbour]) {
                    visited[neighbour] = true;
                    distance[neighbour] = distance[current] + 1;
                    queue.add(neighbour);
                }
            }
        }

        System.out.println("Shortest path: " + distance[target]);
        System.out.println("Reachable attractions: " + reachable);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int e = sc.nextInt();

        ArrayList<ArrayList<Integer>> graph = new ArrayList<>();

        for (int i = 0; i < n; i++)
            graph.add(new ArrayList<>());

        for (int i = 0; i < e; i++) {
            int u = sc.nextInt();
            int v = sc.nextInt();

            graph.get(u).add(v);
            graph.get(v).add(u);
        }

        int start = sc.nextInt();
        int target = sc.nextInt();

        bfs(graph, start, target, n);
    }
}
```

## Output:

<img width="340" height="291" alt="image" src="https://github.com/user-attachments/assets/d92186d9-8979-4b9a-821d-d36b4a9ac013" />


## Result:

The program has been successfully implemented and executed.
It correctly computes:
The shortest number of paths (minimum hops) between two attractions.
The total number of reachable attractions from a given starting point using BFS traversal.
