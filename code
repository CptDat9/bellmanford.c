#include <limits.h>
#include <stdio.h>
#include <stdlib.h>

// Define maximum number of vertices
#define MAX_VERTICES 1000
// Define infinity for initialization
#define INF INT_MAX

// Define Edge structure
typedef struct {
    int source;
    int destination;
    int weight;
} Edge;

// Define Bellman-Ford function
void bellmanFord(int graph[MAX_VERTICES][MAX_VERTICES],
                 int vertices, int edges, int source)
{
    // Declare distance array
    int distance[MAX_VERTICES];

    // Initialize distances from source to all vertices as
    // infinity
    for (int i = 0; i < vertices; ++i)
        distance[i] = INF;
    // Distance from source to itself is 0
    distance[source] = 0;

    // Relax edges V-1 times
    for (int i = 0; i < vertices - 1; ++i) {
        // For each edge
        for (int j = 0; j < edges; ++j) {
            // If the edge exists and the new distance is
            // shorter
            if (graph[j][0] != -1
                && distance[graph[j][0]] != INF
                && distance[graph[j][1]]
                       > distance[graph[j][0]]
                             + graph[j][2])
                // Update the distance
                distance[graph[j][1]]
                    = distance[graph[j][0]] + graph[j][2];
        }
    }

    // Check for negative cycles
    for (int i = 0; i < edges; ++i) {
        // If a shorter path is found, there is a negative
        // cycle
        if (graph[i][0] != -1
            && distance[graph[i][0]] != INF
            && distance[graph[i][1]]
                   > distance[graph[i][0]] + graph[i][2]) {
            printf("Negative cycle detected\n");
            return;
        }
    }

    // Print shortest distances from source to all vertices
    printf("Vertex   Distance from Source\n");
    for (int i = 0; i < vertices; ++i)
        printf("%d \t\t %d\n", i, distance[i]);
}

// Define main function
int main()
{
    // Define number of vertices and edges
    int vertices = 6;
    int edges = 8;

    // Define graph as an array of edges
    int graph[MAX_VERTICES][MAX_VERTICES]
        = { { 0, 1, 5 }, { 0, 2, 7 }, { 1, 2, 3 },
            { 1, 3, 4 }, { 1, 4, 6 }, { 3, 4, -1 },
            { 3, 5, 2 }, { 4, 5, -3 } };

    // Call Bellman-Ford function with source vertex as 0
    bellmanFord(graph, vertices, edges, 0);
    return 0;
}
