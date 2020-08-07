# Dynamic-Programming-on-Trees

Given a tree with N nodes and N-1 edges, calculate the maximum sum of the node values from root to any of the leaves without re-visiting any node.



Given above is a diagram of a tree with N=14 nodes and N-1=13 edges. The values at node being 3, 2, 1, 10, 1, 3, 9, 1, 5, 3, 4, 5, 9 and 8 respectively for nodes 1, 2, 3, 4….14.




The diagram below shows all the paths from root to leaves :



All the paths are marked by different colors :

Path 1(red, 3-2-1-4) : sum of all node values = 10
Path 2(orange, 3-2-1-5) : sum of all node values = 11
Path 3(yellow, 3-2-3) : sum of all node values = 8
Path 4(green, 3-1-9-9) : sum of all node values = 22
Path 5(violet, 3-1-9-8) : sum of all node values = 21
Path 6(pink, 3-10-1) : sum of all node values = 14
Path 7(blue, 3-10-5) : sum of all node values = 18
Path 8(brown, 3-10-3) : sum of all node values = 16

The answer is 22, as Path 4 has the maximum sum of values of nodes in its path from a root to leaves.

The greedy approach fails in this case. Starting from the root and take 3 from the first level, 10 from the next level and 5 from the third level greedily. Result is path-7 if after following greedy approach, hence do not apply greedy approach over here.

The problem can be solved using Dynamic Programming on trees. Start memoizing from the leaves and add the maximum of leaves to the root of every sub-tree. At the last step, there will be root and the sub-tree under it, adding the value at node and maximum of sub-tree will give us the maximum sum of the node values from root to any of the leaves.



The diagram above shows how to start from the leaves and add the maximum of leaves of a sub-tree to its root. Move upward and repeat the same procedure of storing the maximum of every sub-tree leaves and adding it to its root. In this example, the maximum of node 11 and 12 is taken to count and then added to node 5(In this sub-tree, 5 is the root and 11, 12 are its leaves). Similarly, the maximum of node 13 and 15 is taken to count and then added to node 7. Repeat the steps for every sub-tree till we reach the node.

Let DPi be the maximum summation of node values in the path between i and any of its leaves moving downwards. Traverse the tree using DFS traversal. Store the maximum of all the leaves of the sub-tree, and add it to the root of the sub-tree. At the end, DP1 will have the maximum sum of the node values from root to any of the leaves without re-visiting any node.

Below is the implementation of the above idea :
