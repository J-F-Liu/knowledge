# Graph Theory

A graph is made up of vertices (also called nodes or points) which are connected by edges (also called links or lines).

A directed graph (or digraph) is a graph that is made up of a set of vertices connected by edges, where the edges have a direction associated with them.

A graph is said to be strongly connected if every vertex is reachable from every other vertex.

A complete graph is a simple undirected graph in which every pair of distinct vertices is connected by a unique edge.

A complete digraph is a directed graph in which every pair of distinct vertices is connected by a pair of unique edges (one in each direction).

A clique is a subset of vertices of an undirected graph such that every two distinct vertices in the clique are adjacent; that is, its induced subgraph is complete.

The opposite of a clique is an independent set, i.e. a set of vertices in a graph, no two of which are adjacent.

## Route Problems

The shortest path problem is the problem of finding a path between two vertices (or nodes) in a graph such that the sum of the weights of its constituent edges is minimized.

The route inspection problem is to find a shortest closed path or circuit that visits every edge of a (connected) undirected graph.

The travelling salesman problem is to find a shortest closed path or circuit that visits every node of a (connected) edge-weighted undirected graph.

The Hamiltonian path problem and the Hamiltonian cycle problem are problems of determining whether a Hamiltonian path (a path in an undirected or directed graph that visits each vertex exactly once) or a Hamiltonian cycle exists in a given graph (whether directed or undirected).

## Subgraphs

A minimum spanning tree (MST) or minimum weight spanning tree is a subset of the edges of a connected, edge-weighted undirected graph that connects all the vertices together, without any cycles and with the minimum possible total edge weight.

A maximal clique is a clique that cannot be extended by including one more adjacent vertex, that is, a clique which does not exist exclusively within the vertex set of a larger clique. Some authors define cliques in a way that requires them to be maximal, and use other terminology for complete subgraphs that are not maximal.

A maximum clique of a graph, G, is a clique, such that there is no clique with more vertices. Moreover, the clique number ω(G) of a graph G is the number of vertices in a maximum clique in G.
