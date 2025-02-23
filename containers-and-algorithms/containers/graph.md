# Graph

## Terminology

**General terminology**
- Node/vertex $v$: an entity containing some information, depicted as a circle containing some information
- Edge $(u, v)$: a connection between two nodes, depicted an arrow between two vertices 
- Path: a sequence of nodes $(v_1 , v_2, \dots, v_k)$ such that $(v_i, v_{i + 1})$ is an edge
- Path length: number of edges in the path, or equivalently, number of nodes in the path minus one

**Rooted tree specific terminology**
- Tree: an undirected connected graph with no cycles, with $N$ nodes and $N - 1$ edges
- Rooted tree: a tree with a designated root node
- Root node: topmost node in the tree
- Parent node: node with one or more child nodes
- Child node: node pointed by a single node above (its parent), except the root
- Sibling node: node with the same parent
- Leaf/external node: node without children nodes
- Internal node: node with children nodes
- Ancestor and descendent of a node:  $v$ is an ancestor of $w$ if there is a path from $v$ to $w$, while $v$ would be considered the descendent of $w$
- Depth/level of a node: number of edges from the root to the node
- Height of a node: number of edges from the node to the deepest leaf
- Height of a tree: height of the root node
- Binary tree: a rooted tree for which every node has at most two child nodes
- Binary search tree: a binary tree which satisfy the BST invariant which states that for every node $x$, all nodes to the left of $x$ must have keys less than $x$'s key, while all nodes to the right must have keys greater than $x$'s key
- Full tree: binary tree in which each node has exactly zero or $N$ children nodes
- Complete tree: binary tree, which is completely filled, with the possible exception of the bottom level, which is filled from left to right

**Graph specific terminology**

## Operations

| **Operation**                                     | **Description**                                                             |
| ------------------------------------------------- | --------------------------------------------------------------------------- |
| `get_vertices()`                                  | Retrieves all the vertices present in the graph.                            |
| `get_edges()`                                     | Retrieves all the edges present in the graph.                               |
| `get_neighbors(vertex: V)`                        | Returns a list of neighboring vertices connected to the specified vertex.   |
| `add_vertex(vertex: V)`                           | Adds a new vertex to the graph.                                             |
| `add_edge(vertex_1: V, vertex_2: V, weight: Int)` | Creates a new edge between `vertex_1` and `vertex_2` with the given weight. |
| `contains_vertex(vertex: V)`                      | Checks if the specified vertex exists in the graph.                         |
| `contains_edge(vertex_1: V, vertex_2: V)`         | Checks if an edge exists between `vertex_1` and `vertex_2`.                 |
| `remove_vertex(vertex: V)`                        | Removes the specified vertex and all associated edges from the graph.       |
| `remove_edge(vertex_1: V, vertex_2: V)`           | Removes the edge between `vertex_1` and `vertex_2` from the graph.          |

also get/set vertex value and edge weight


