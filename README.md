/*******Binary trees*********/

___Learning Objectives___
a. What is a binary tree
	- is a type of data structure where each parent node can have at most two child nodes.
b. What is the difference between a binary tree and a Binary Search Tree:
	- A binary search tree (BST), also called an ordered or sorted binary tree, is a rooted binary tree data structure with the key of each internal node being greater than all the keys in the respective node's left subtree and less than the ones in its right subtree.
	- Binary search trees allow binary search for fast lookup, addition, and removal of data items.
	- The performance of a binary search tree is dependent on the order of insertion of the nodes into the tree since arbitrary insertions may lead to degeneracy; several variations of the binary search tree can be built with guaranteed worst-case performance. The basic operations include: search, traversal, insert and delete.
	- 
c. What is the possible gain in terms of time complexity compared to linked lists
d. What are the depth, the height, the size of a binary tree
e. What are the different traversal methods to go through a binary tree
	- Depending on the order in which we do this, there can be three types of traversal.
	- Inorder traversal
	- Postorder traversal
	- Preorder traversal
f. What is a complete, a full, a perfect, a balanced binary tree.
	- A complete binary tree is a binary tree in which every level, except possibly the last, is completely filled, and all nodes in the last level are as far left as possible.
	- A full binary tree (sometimes referred to as a proper[15] or plane or strict binary tree)[16][17] is a tree in which every node has either 0 or 2 children.
	- A balanced binary tree is a binary tree structure in which the left and right subtrees of every node differ in height by no more than 1.

A binary tree is  a k = 2 tree data structure in which each node has at most two children.(ref to as the left & right children).
When we have a missing child we set the pointer to null
A strict binary tree if it has two or 0 children.
A complete binary tree if all levels except the nodes at the last level possibly and all nodes are as left as possible.
Max depth of a tree is equal to the height of the tree.
Max no. of nodes at a level i, i = 2^i
A perfect binary tree has all nodes filled in each level

Properties of binary trees
Types of binary trees
A binary tree has the benefits of both an ordered array and a linked list as search is as quick as in a sorted array and insertion or deletion operation are as fast as in linked list.

Path − Path refers to the sequence of nodes along the edges of a tree.

Root − The node at the top of the tree is called root. There is only one root per tree and one path from the root node to any node.

Parent − Any node except the root node has one edge upward to a node called parent.

Child − The node below a given node connected by its edge downward is called its child node.

Leaf − The node which does not have any child node is called the leaf node.

Subtree − Subtree represents the descendants of a node.

Visiting − Visiting refers to checking the value of a node when control is on the node.

Traversing − Traversing means passing through 
nodes in a specific order.

Levels − Level of a node represents the generation of a node. If the root node is at level 0, then its next child node is at level 1, its grandchild is at level 2, and so on.

keys − Key represents a value of a node based on which a search operation is to be carried out for a node.

Tree Node
The code to write a tree node would be similar to what is given below. It has a data part and references to its left and right child nodes.

struct node {
   int data;   
   struct node *leftChild;
   struct node *rightChild;
};

The basic operations that can be performed on a binary search tree data structure, are the following −

Insert − Inserts an element in a tree/create a tree.

Search − Searches an element in a tree.

Preorder Traversal − Traverses a tree in a pre-order manner.

Inorder Traversal − Traverses a tree in an in-order manner.

Postorder Traversal − Traverses a tree in a post-order manner.

Insert Operation
The very first insertion creates the tree. Afterwards, whenever an element is to be inserted, first locate its proper location. Start searching from the root node, then if the data is less than the key value, search for the empty location in the left subtree and insert the data. Otherwise, search for the empty location in the right subtree and insert the data.

The insertion Algorithm :

If root is NULL 
   then create root node
return

If root exists then
   compare the data with node.data
   
   while until insertion position is located

      If data is greater than node.data
         goto right subtree
      else
         goto left subtree

   endwhile 
   
   insert data
	
end If

Implementation
The implementation of insert function should look like this −

void insert(int data) {
   struct node *tempNode = (struct node*) malloc(sizeof(struct node));
   struct node *current;
   struct node *parent;

   tempNode->data = data;
   tempNode->leftChild = NULL;
   tempNode->rightChild = NULL;

   //if tree is empty, create root node
   if(root == NULL) {
      root = tempNode;
   } else {
      current = root;
      parent  = NULL;

      while(1) {                
         parent = current;

         //go to left of the tree
         if(data < parent->data) {
            current = current->leftChild;                
            
            //insert to the left
            if(current == NULL) {
               parent->leftChild = tempNode;
               return;
            }
         }
			
         //go to right of the tree
         else {
            current = current->rightChild;
            
            //insert to the right
            if(current == NULL) {
               parent->rightChild = tempNode;
               return;
            }
         }
      }            
   }
}

Search Operation
Whenever an element is to be searched, start searching from the root node, then if the data is less than the key value, search for the element in the left subtree. Otherwise, search for the element in the right subtree. Follow the same algorithm for each node.

Algorithm
If root.data is equal to search.data
   return root
else
   while data not found

      If data is greater than node.data
         goto right subtree
      else
         goto left subtree
         
      If data found
         return node
   endwhile 
   
   return data not found
   
end if     

The implementation of this algorithm should look like this.

struct node* search(int data) {
   struct node *current = root;
   printf("Visiting elements: ");

   while(current->data != data) {
      if(current != NULL)
      printf("%d ",current->data); 
      
      //go to left tree

      if(current->data > data) {
         current = current->leftChild;
      }
      //else go to right tree
      else {                
         current = current->rightChild;
      }

      //not found
      if(current == NULL) {
         return NULL;
      }
   }
   return current;
}


