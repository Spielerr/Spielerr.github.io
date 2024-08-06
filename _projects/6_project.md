---
layout: page
title: Implementation of Treaps
description: a C++ project built using OOPS techniques
img: assets/img/treaps.jpeg
importance: 6
category: work
---

[[Project Report]]({{ '/assets/pdf/Generic_Programming_Project_Report.pdf' | relative_url }})
[[Project Readme]]({{ '/assets/pdf/Generic_Programming_Project_Readme.pdf' | relative_url }})
[[Code]](https://github.com/Spielerr/Implementation-of-Treaps)

### Summary
A project aimed at implementing Treap as a generic data structure along with the different functionalities of a Treap. Treap is a data structure that stores pairs (say [X, Y]) in a binary tree such that it is a binary search tree by X and a binary heap by Y. In such an implementation, the X values are the keys, while the Y values are the priorities that specify how the tree is constructed. In this project, the priorities are randomized, thereby using Randomization and the Binary Heap property (specifically, the max heap property in our implementation) to construct a randomized, balanced binary search tree that maintains balance with high probability. The entire treap and its individual nodes were built as generic canonical classes, thereby supporting all the different data types. The project involved the implementation of multiple operations such as insert node, delete node, split treap, merge two treaps, union, intersection, difference, and traversal of treaps. A bidirectional iterator was implemented as a nested class within the treap class. Multiple member algorithms, such as find and replace were implemented for treaps. This project was developed and implemented as part of the Generic Programming Course during my Undergraduate Study.

### Implementation Details
The treap data structure and its operations have been implemented as part of a header file that the user can include as a library in their client files to invoke and use treap as a generic container. The treap data structure has been implemented using C++ templates to make it a generic container that can support all data types.

Each node of the treap has been represented as a generic class with the following attributes:

* Pair of key and priority
* Pointer to left child of the node
* Pointer to right child of the node
* An implementation field to mark a node as a duplicate
This Treap_node class has been made canonical by providing a constructor, a copy constructor, a copy assignment operator, and a destructor.

The Treap itself has been represented as a generic class with the following attributes:

* Pointer to the root of the treap
* An implementation field to decide the way in which the priorities are defined. By default, the priorities are assigned randomly
* An implementation field to store all the previously defined priorities to ensure that the priorities are not repeated for different nodes.
The Treap class has been made canonical by providing a constructor, a copy constructor, a copy assignment operator, and a destructor. Further, a special constructor called the build constructor has been provided that takes in a pair of iterators pointing to a collection of data items and creates a Treap consisting of these data items in linear time.

### Operations that can be performed on a Treap:
#### Insert Node

The insert node function allows for the insertion of a new node with a key value into the Treap. The function inserts this new node into the Treap by adhering to the binary search property based on the key of the node while adhering to the binary heap property based on the randomly generated priority for this node. Consequently, left and right rotations are performed appropriately to ensure that the binary heap property is maintained.

#### Delete Node

The delete node function allows for the deletion of a node with a particular key value from the Treap. The binary search tree property is used to search for the node with the given key value. If this node is found in the treap, there are different actions performed based on the number of children of this node, as explained below:

* If the node to be deleted is a leaf node, it can be deleted and freed directly.
* If the node to be deleted has one child, then the node to be deleted is replaced with this child node, and the node to be deleted is deleted and freed.
* If the node to be deleted has two children, then the nodes are rotated appropriately while maintaining the binary heap property to ensure that the node to be deleted is rotated with one of the child nodes. Subsequently, the delete node function is called recursively on the node to be deleted, thereby pushing the node down the tree by performing rotations and finally deleting the node when it becomes a leaf or has only one child.

#### Split Treap

The split function separates the given tree into two sub-trees based on the given key value. The given key need not be present in the tree. The subtrees that are generated after the split operation are such that one subtree will have all its nodes lesser than the given key value, and the other subtree will have all its nodes greater than or equal to the given key value. This operation is implemented by making use of the previously defined insert function. The given key is inserted as a node in the tree such that the key will have the highest priority and, hence, will undergo rotations to become the root. Now that the given key is the root, if the given key was not already a part of the original tree, the tree is split by assigning the two subtrees as the new split trees. If the given key was present in the tree, the tree is split in the same aforementioned way, but it is ensured that the root is not deleted and is assigned to the right subtree.

#### Merge Treaps

The Merge function combines the given two trees while maintaining the Binary Search and Binary Heap property and finally returns the new combined tree. It is implemented under the assumption that the elements of the left subtree are all lesser than the elements of the right subtree. Thus, as the Binary Search property is already satisfied by the pre-condition, it only needs to be ensured that the priorities of the merged tree follow the binary heap property. Recursion has been used to merge the two trees. If both the trees are empty, an empty tree is returned as the merged tree. If either of the trees is empty, the other tree is returned as the merged tree. These form the base condition of the recursion. During recursion, if the root of the left tree has a higher priority than that of the right tree, a recursive merge call is invoked on the right node of the left tree and the root of the right tree, and the result would be assigned to the right node of the left tree which would then be assigned to the merged tree pointer. Similarly, if the root of the right tree has a higher priority than that of the left subtree, a recursive merge call is invoked on the left node of the right tree and the root of the left tree, and the result would be assigned to the left node of the right tree which would then be assigned to the merged tree pointer.

#### Union of Treaps

The Union functionality is equivalent to the set union operation. The function follows a divide-and-conquer approach. To maintain the max heap property, it is ensured that the root of the resultant tree (say r) is the root of the subtrees with the largest priority. Let’s consider that the key of this root is k. To maintain the BST order, the other sub-tree whose root had a lesser priority is split into two subtrees, which are ordered, that is, the left split will have all values < k, and the right split will have all values >= k. The union operation is then recursively invoked to find the union of the left child of r and the left split of the other tree and then to find the union of the right child of r and the right split of the other tree. The resultant of the two calls become the left and right subtrees of r, respectively.

#### Intersection of Treaps

The Intersection functionality is equivalent to the set intersection operation. As with the union operation, the intersection operation starts by splitting the treap with the smaller priority root by k, which is the key of the root with the greater priority. It then finds the intersection of the two left subtrees, which have keys less than k, and the intersection of the two right subtrees, which have keys greater than k. If k appeared in both the trees, then these results become the left and right children of the root used to split. Otherwise, it returns the join of the two recursive call results.

#### Difference of Treaps

The Difference functionality is equivalent to the set difference operation. The new tree contains the elements of the first tree that are not in the second tree. To find the difference of two treaps T1 and T2, the difference operation splits the treap with the smaller priority root by k, which is the key of the root of the other treap. Then, it finds the difference of the two left subtrees, which have keys less than k, and the difference of the two right subtrees, which have keys greater than k. As the difference operation is not symmetric, the difference operation considers two cases - when T2 is the subtrahend (the set specifying what should be removed) and when T2 is not, as specified by the boolean rt_subt. If T2 is the subtrahend and it does not contain k, then it sets the left and right children of the root of T1 to the results of the recursive calls and returns this root. Otherwise, it returns the join of the results of the recursive calls.

#### Travesal of Treap

The preorder traversal, postorder traversal, and inorder traversal of the treap have been implemented as part of the project.

#### Iterator

A bidirectional iterator has been provided for the Treap data structure, supporting the following operations: pre-increment, post-increment, pre-decrement, post-decrement, deference, equality, and inequality operations. Further, the begin operation to return an iterator pointing to the first node of the treap based on the inorder traversal and the end operation to return an iterator initialized with nullptr have been implemented as part of the treap data structure.

### Member Algorithms

A few member algorithms have been implemented as follows:

* **Member Find**: If the generic find algorithm is called on treap, the complexity of the find operation would be linear [O(n)] as it would use the increment operator, which would make use of the inorder successor at every point. Member find has been implemented to use the binary search property to search for a node such that the complexity of the find operation becomes log(n).
* **Member Replace**: If the generic replace algorithm is called on treap, once the key of a node is replaced with a new key, the binary search tree property and the max heap property of the treap may be broken. The member replace algorithm replaces the key with the new key value mentioned by doing the following. It first deletes the node containing the old key value. It then inserts a new node with the new key value. The insert function takes care of all the rotations to ensure that the binary search tree property and the max heap property of the treap are maintained.
Further, different generic algorithms can be invoked for the treap by utilizing the iterators of the treap.