#include <stdio.h>
#include <stdlib.h>

#define MAX 100

int time = 0;
int disc[MAX], low[MAX], parent[MAX], ap[MAX];
int adj[MAX][MAX];

// Function to perform DFS traversal and check for articulation points
void DFS(int u, int V) {
    disc[u] = low[u] = ++time;
    int children = 0;
    for (int v = 0; v < V; v++) {
        if (adj[u][v] == 1) {
            if (disc[v] == -1) { // If v is not visited
                parent[v] = u;
                DFS(v, V);
                low[u] = (low[u] < low[v]) ? low[u] : low[v];
                if (parent[u] == -1 && ++children > 1) {
                    ap[u] = 1; // u is an articulation point
                }
                if (parent[u] != -1 && low[v] >= disc[u]) {
                    ap[u] = 1; // u is an articulation point
                }
            }
            else if (v != parent[u]) {
                low[u] = (low[u] < disc[v]) ? low[u] : disc[v];
            }
        }
    }
}

// Function to check biconnectivity
void biconnected(int V) {
    for (int i = 0; i < V; i++) {
        disc[i] = low[i] = -1;
        parent[i] = -1;
        ap[i] = 0;
    }
    for (int i = 0; i < V; i++) {
        if (disc[i] == -1) {
            DFS(i, V);
        }
    }

    // Print articulation points
    printf("Articulation points are: ");
    for (int i = 0; i < V; i++) {
        if (ap[i]) {
            printf("%d ", i);
        }
    }
    printf("\n");
}

int main() {
    int V = 5; // Number of vertices
    adj[0][1] = adj[1][0] = 1;
    adj[1][2] = adj[2][1] = 1;
    adj[2][3] = adj[3][2] = 1;
    adj[3][4] = adj[4][3] = 1;

    biconnected(V);

    return 0;
}
