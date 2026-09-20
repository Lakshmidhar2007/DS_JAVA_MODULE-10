# Ex23 Breadth-First Search (BFS) Traversal of a City Junction Map

## DATE: 20/09/2026

## AIM:

To design and implement a Java program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph, and find all reachable locations from a given source junction.

## Algorithm

1. Read the number of vertices and edges of the graph.
2. Create an adjacency list to represent the connections between junctions.
3. Read the edges and add the connected junctions to the adjacency list.
4. Start BFS from the given source node using a queue and mark each visited node.
5. Remove nodes from the queue, visit their unvisited neighbours, and display the BFS traversal.

## Program:

```java id="y4h1n8"
/*
Program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph
Developed by: LAKSHMIDHAR N
RegisterNumber:  212224230138
*/

import java.util.*;

public class Main {

    static void bfs(ArrayList<ArrayList<Integer>> graph, int source, int n) {
        boolean[] visited = new boolean[n];
        Queue<Integer> queue = new LinkedList<>();

        visited[source] = true;
        queue.add(source);

        while (!queue.isEmpty()) {
            int current = queue.poll();
            System.out.print(current + " ");

            for (int neighbour : graph.get(current)) {
                if (!visited[neighbour]) {
                    visited[neighbour] = true;
                    queue.add(neighbour);
                }
            }
        }
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

        int source = sc.nextInt();

        bfs(graph, source, n);
    }
}
```

## Output:

<img width="366" height="228" alt="image" src="https://github.com/user-attachments/assets/7ff827be-fac3-48a7-a928-6397b5ceabd5" />


## Result:

The program has been successfully implemented and executed.
It performs Breadth-First Search (BFS) traversal on a city junction map and correctly lists all reachable locations from the given source node.
