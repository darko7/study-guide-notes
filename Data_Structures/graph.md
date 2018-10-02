Graphs

How do we define a graph matematically?
G = (V, E)

 What is the maximum number of edges in a directed simple graph? Undirected simple graph? Answer should be in terms of N
 Directed N(N - 1)
Undirected (N(N - 1)) / 2

 What are some naive ways we can store and traverse graphs? Be able to discuss time/space complexity of these approaches, and what issues we may face.
 In undirected graph,  we store the vertices in a set and the edges in an object which contains edge objects (unordered pairs).
In directed graph, we store the vertices in the same way but the edges is an object which contains ordered pairs where (origin node is the first)

 Give an example of various types of graphs (Weighted Undirected, Unweighted Directed, Unweighted Undirected, etc.)
 Facebook (undirected graph), Twitter (directed), Websites where you can go to different links, Flights (directed and weighted because they carry prize)

 If we were only concerned about space complexity, is an Adjacency Matrix efficient? Why/why not?
 It's efficient only if the graph is dense or the number of vertices is too less to matter

  If we were only concerned about time complexity, is an Adjacency Matrix efficient? Why/why not?
  If we are concerned about finding if two nodes are connected then yes it is, otherwise it's O(v) which in case where number of v is huge then no.

  Give a high level overview of an Adjacency Matrix
  Adjacency matrix is a square matrix used to represent a finite graph. The elements of the matrix indicate whether pairs of vertices are adjacent or not in the graph.
In the special case of a finite simple graph, the adjacency matrix is a (0,1)-matrix with zeros on its diagonal. If the graph is undirected, the adjacency matrix is symmetric.

What benefits do we get from an Adjacency List?
Much less memory than the matrix, and also better time complexity in most of the cases

Give a high level overview of an Adjacency List
Adjacency list is a collection of unordered lists used to represent a finite graph. Each list describes the set of neighbors of a vertex in the graph. This is one of several commonly used representations of graphs for use in computer programs. It has a better space complexity, and in most of the cases better time complexity