# Ex25 Finding the Fastest Route to a Charging Station using Dijkstra’s Algorithm

## DATE: 20/09/2026

## AIM:

To design and implement a Java program that helps an electric vehicle (EV) find the shortest travel time from its current block to the nearest charging station using Dijkstra’s shortest path algorithm.

## Algorithm

1. Read the number of blocks, roads, and charging stations, and create a weighted graph.
2. Store the travel time of each road in the adjacency list.
3. Use Dijkstra’s algorithm to calculate the shortest distance from the EV’s current block to all other blocks.
4. Check the shortest distance to each charging station and find the minimum travel time.
5. Display the shortest travel time to the nearest reachable charging station; if none is reachable, display an appropriate message.

## Program:

```java
/*
Program to find the Fastest Route to a Charging Station using Dijkstra’s Algorithm
Developed by: LAKSHMIDHAR N
RegisterNumber:  212224230138
*/

import java.util.*;

public class Main {

    static class Edge {
        int node, weight;

        Edge(int node, int weight) {
            this.node = node;
            this.weight = weight;
        }
    }

    static int[] dijkstra(ArrayList<ArrayList<Edge>> graph, int source) {
        int n = graph.size();
        int[] dist = new int[n];

        Arrays.fill(dist, Integer.MAX_VALUE);
        dist[source] = 0;

        PriorityQueue<Edge> pq =
                new PriorityQueue<>((a, b) -> a.weight - b.weight);

        pq.add(new Edge(source, 0));

        while (!pq.isEmpty()) {
            Edge current = pq.poll();
            int u = current.node;

            if (current.weight > dist[u])
                continue;

            for (Edge edge : graph.get(u)) {
                int v = edge.node;
                int newDist = dist[u] + edge.weight;

                if (newDist < dist[v]) {
                    dist[v] = newDist;
                    pq.add(new Edge(v, newDist));
                }
            }
        }

        return dist;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int e = sc.nextInt();

        ArrayList<ArrayList<Edge>> graph = new ArrayList<>();

        for (int i = 0; i < n; i++)
            graph.add(new ArrayList<>());

        for (int i = 0; i < e; i++) {
            int u = sc.nextInt();
            int v = sc.nextInt();
            int time = sc.nextInt();

            graph.get(u).add(new Edge(v, time));
            graph.get(v).add(new Edge(u, time));
        }

        int source = sc.nextInt();

        int stations = sc.nextInt();
        int[] chargingStations = new int[stations];

        for (int i = 0; i < stations; i++)
            chargingStations[i] = sc.nextInt();

        int[] dist = dijkstra(graph, source);

        int minTime = Integer.MAX_VALUE;

        for (int station : chargingStations) {
            if (dist[station] < minTime)
                minTime = dist[station];
        }

        if (minTime == Integer.MAX_VALUE)
            System.out.println("No charging station is reachable");
        else
            System.out.println("Shortest travel time: " + minTime);
    }
}
```

## Output:

<img width="577" height="362" alt="image" src="https://github.com/user-attachments/assets/0273acd0-b67e-47f8-b7d7-573195aa7eb9" />


## Result:

The program has been successfully implemented and executed.
It uses Dijkstra’s algorithm to determine the shortest travel time from the EV’s current location to the nearest charging station and correctly handles cases where no station is reachable.
