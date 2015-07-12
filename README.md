Data Structures Project: C++ Implementation of AVL Tree
-------------------------------------------------------

###Algorithm:

**Insertion:**  
1) Perform the normal BST insertion.  
2) The current node must be one of the ancestors of the newly inserted node. Update the height of the current node.  
3) Get the balance factor (left subtree height – right subtree height) of the current node.  
4) If balance factor is greater than 1, then the current node is unbalanced and we are either in Left Left case or Left Right case. To check whether it is left left case or not, compare the newly inserted key with the key in left subtree root.  
5) If balance factor is less than -1, then the current node is unbalanced and we are either in Right Right case or Right Left case. To check whether it is Right Right case or not, compare the newly inserted key with the key in right subtree root.  

**Deletion:**  
Delete(T,k) means delete a node with the key k from the AVL tree T  
I) Find the node x where k is stored  
II) Delete the contents of node x   

There are three possible cases (just like for BSTs):  
1) If x has no children (i.e., is a leaf), delete x.  
2) If x has one child, let x' be the child of x.  
    	Notice: x' cannot have a child, since sub-trees of T can differ in height by at most one  
    		-replace the contents of x with the contents of x'  
  		 -delete x' (a leaf)   
3) If x has two children,   
  		 -find x's successor z (which has no left child)  
   		-replace x's contents with z's contents, and   
   		-delete z.  
   		[Since z has at most one child, so we use case (1) or (2) to delete z]  
    	In all 3 cases, we end up removing a leaf.  
    	
 III) Go from the deleted leaf towards the root and at each ancestor of that leaf:  
      	-update the balance factor  
      	-rebalance with rotations if necessary.  
  
**To perform a left rotation:**  
1.	Promote the right child (B) to be the root of the subtree.  
2.	Move the old root (A) to be the left child of the new root.  
3.	If new root (B) already had a left child then make it the right child of the new left child (A). Note: Since the new root (B) was the right child of A the right child of A is guaranteed to be empty at this point. This allows us to add a new node as the right child without any further consideration.  

**To perform a right rotation:**  
1.	Promote the left child (C) to be the root of the subtree.  
2.	Move the old root (E) to be the right child of the new root.  
3.	If the new root(C) already had a right child (D) then make it the left child of the new right child (E). Note: Since the new root (C) was the left child of E, the left child of E is guaranteed to be empty at this point. This allows us to add a new node as the left child without any further consideration.  

