# Data Structure

* [Array vs Linked List](#Array-vs-Linked-List)
* [Stack and Queue](#Stack-and-Queue)
* [Tree](#Tree)
  * Binary Tree
  * Perfect Binary Tree
  * Complete Binary Tree
  * Full Binary Tree
  * BST(Binary Search Tree) 
* [Binary Heap](#Binary-Heap)
* [Red Black Tree](#Red-Black-Tree)
  * Definition of Red-Black Tree
  * Characteristics of Red-Black Tree
  * Insertion
  * Delete

</br>

## Array vs Linked List

</br>

### Array
  
</br>

The most basic data structure, the Array data structure, has the same logical and physical storage order. Therefore, you can access the element by index. Therefore, if you know the index value of the element you are looking for, you can access Big-O(1) as the element. In other words, it has the advantage that random access is possible.

However, in the process of deleting or inserting, it takes more time because you have to access the element and complete the task (O(1)), and then perform another task additionally. If an element of an array is deleted, the successive characteristics of the array are broken. In other words, there is an empty space. Therefore, the cost of shifting elements having an index larger than the deleted element is incurred, and the time complexity in this case becomes O(n). Therefore, the worst case of the time complexity for the delete function in the Array data structure is O(n).

The same is true for insertion. If you want to add a new element to the first digit, you need to shift the indexes of all elements by 1, so in this case, it also requires O(n) time.

</br>

### Linked List

</br>

The data structure for solving this problem is a linked list. Each element only remembers what element it is after itself. Therefore, if only this part is changed to a different value, deletion and insertion can be solved in O(1).

However, linked lists also have one problem. If you want to insert at a desired position, you have to check all the first elements in the search process for the desired position. This is because the logical storage order and physical storage order do not match, unlike Array. This is like inserting and sorting once. Because of this process, when an element is deleted or added, O(n) time is additionally generated to find the element.

After all, the linked list data structure has O(n) time complexity for search and O(n) time complexity for insertion and deletion. This is not a very useless data structure, so we are learning. This Linked List is a data structure that is the basis of the Tree structure, and its usefulness is revealed when used in Tree.

</br>

## Stack and Queue

</br>

### Stack

</br>

Last In First Out (LIFO) as a type of linear data structure. In other words, the element entered later comes out first. This is the biggest feature of the Stack. It is a structure that stacks up one by one, and the elements that first enter the stack are laid on the bottom. Therefore, the ones who entered late are piled up on top of them, and the top one is called when calling.

### Queue

</br>

First In First Out (FIFO) as a type of linear data structure. That is, the one who entered first comes out first. Contrary to the stack, the person who entered first waits at the front, and then comes out first. For reference, in Java Collection, Queue is an interface. Priority queues that implement this can be used.

</br>

## Tree

</br>

### Binary Tree

</br>

It is divided into two sub-trees (a small tree belonging to a large tree) around the root node. Also, both divided subtrees must be binary trees. It seems that it is a recursive definition, but it does not seem to be easy to understand. As an addition, we need to include the empty set as a binary tree. This is because the definition is satisfied when the condition is checked recursively and when it is attached to the leaf node. Naturally, even having only one node is satisfied with the binary tree definition.

In the tree, each layer is numbered and called the level of the tree. The level value starts from 0, so the level of the root node is 0. And, referring to the highest level of the tree, it is called the height of the tree.

</br>

### Perfect Binary Tree, Complete Binary Tree, Full Binary Tree

</br>

A binary tree full of all levels is called a saturated binary tree. A binary tree that is filled in order from top to bottom and left to right is called a complete binary tree. A binary tree in which all nodes have only 0 or 2 child nodes is called a positive binary tree. In a binary tree consisting of an array, when the number of nodes is n and the root starts at 1 instead of 0, parent(i) = i/2, left_child(i) = 2i, right_child(i) = 2i + for the i-th node. It has an index value of 1.

### BST(Binary Search Tree)
For an efficient search, you shouldn't just worry about how to find it. Rather, we have to think about what is the storage method for efficient search. The binary search tree is a kind of binary tree. However, there are rules for storing data in the binary search tree. And that rule can be used to locate specific data.

- Rule 1. The keys stored in nodes of the binary search tree are unique.
- Rule 2. The height of the parent is greater than the height of the left child node.
- Rule 3. The parent's key is less than the right child node's key.
- Rule 4. The left and right subtrees are also binary search trees.

The search operation of a binary search tree has a time complexity of O(log n). In fact, to be precise, it is correct to express it as O(h). This is because the number of nodes that can be added doubles as the height of the tree increases one by one. However, such a binary search tree can be a Skewed Tree. This is because nodes are continuously added to only one side according to the storage order. In this case, it affects the performance, becomes the Worst Case of the search, and the time complexity becomes O(n).

Although it uses more memory than an array and stores data, there is an inefficient situation where the time complexity required for search becomes the same. To solve this problem, a rebalancing technique appeared. The rebalancing of the tree structure for balancing is called rebalancing. There are several types of trees that implement this technique, and one of them is the Red-Black Tree

</br>

## Binary Heap

</br>

As a kind of data structure, it is in the form of a tree, and among the trees, it is a Complete Binary Tree based on an array. When putting the values ​​of the tree into the array, the 0th is skipped and the root node starts from the 1st index. This is to reduce confusion by matching the unique number value of the node and the index of the array. There are two types of heap: max heap and min heap.

Max Heap refers to a complete binary tree where the value of each node is greater than or equal to the value of the children. (Min Heap is the opposite.)

In Max Heap, the value in the root node is the largest, so the time complexity of the operation required to find the maximum value is O(1). And because it is a complete binary tree, it can be managed efficiently using an array. (In other words, random access is possible. In Min heap, the time complexity of the operation required to find the minimum value is O(1).) However, in order to keep the structure of the heap, another node to replace the removed root node is required. . Here, the heap replaces the last node with the root node and then goes through heapify again to maintain the heap structure. In this case, the maximum or minimum value can be approached with a time complexity of O(log n).


</br>

## Red Black Tree

RBT (Red-Black Tree) is a tree-type data structure based on BST. To start with the conclusion, when data is saved in the Red-Black Tree, O(log n) time complexity is required for Search, Insert, and Delete. When the number of nodes is the same, the key idea is to minimize the depth to reduce the time complexity. When the number of nodes is the same, the minimum depth is when the tree is a complete binary tree.

</br>

### Definition of Red-Black Tree

Red-Black Tree is a BST that satisfies the following properties.

1. Each node has a color of red or black.
2. The color of the root node is Black.
3. Each leaf node is black.
4. If a node's color is red, the color of both children is black.
5. For each node, the simple path from node to descendant leaves all contains the same number of black nodes. This is called the Black-Height of the corresponding node.  
> Black-Height: The number of black nodes on a simple path from node x to leaf node not including node x

### Characteristics of Red-Black Tree

As it is a binary search tree, it has all the features of BST.
Among all the paths from the root node to the leaf node, the size ratio of the minimum and maximum paths is not greater than 2. This state is called the balanced state.
If there is no child of the node, the pointer to child stores the NIL value. These NILs are regarded as leaf nodes.
RBT is a data structure created to solve problems that may occur in the process of inserting and deleting BST. How did you solve this?


### Insertion
First, a node is inserted while maintaining the characteristics of BST. Then, the color of the inserted node is set to RED. The reason for designating it as red is to minimize the change of Black-Height. As a result of the insertion, if the RBT characteristic is in violation, the color of the node is adjusted. If the Black-Height is violated, the height is adjusted through rotation. Through this process, the black-height of the internal nodes existing at the same height of the RBT becomes the same, and the size ratio of the minimum path and the maximum path is maintained below 2.

### Delete
Like insertion, deletion also deletes the corresponding node while maintaining the characteristics of BST. The rotation method varies depending on the number of children of the node to be deleted. And, if the color of the deleted node is Black, rotate so that 1 black node is added to the path where the Black-Height decreases by 1, and adjust the color of the node. If the color of the deleted node is red, no Violation occurs, so RBT is maintained.

> ArrayList in Java Collection is also internally composed of RBT, and is also used in Separate Chaining in HashMap. It is an important data structure with good efficiency.