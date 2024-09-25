# Java-Implementation-of-a-Binary-Search-Tree
Java Implementation of a Binary Search Tree
class Node {
int value;
Node left, right;
public Node(int value) {
this.value = value;
left = right = null;
}
}
// Binary Search Tree class
class BinarySearchTree {
Node root;
// Constructor
public BinarySearchTree() {
root = null;
}
// Insert a node into the BST
void insert(int value) {
root = insertRec(root, value);
}
// Recursive method to insert a new value in the BST
Node insertRec(Node root, int value) {
27
// If the tree is empty, create a new node
if (root == null) {
root = new Node(value);
return root;
}
// Otherwise, recur down the tree
if (value < root.value) {
root.left = insertRec(root.left, value);
} else if (value > root.value) {
root.right = insertRec(root.right, value);
}
// Return the unchanged root node
return root;
}
// Search a value in the BST
boolean search(int value) {
return searchRec(root, value);
}
// Recursive method to search for a value
boolean searchRec(Node root, int value) {
// Base Cases: root is null or value is present at root
if (root == null || root.value == value) {
return root != null;
}
// Value is greater than root's value
if (root.value < value) {
return searchRec(root.right, value);
28
}
// Value is less than root's value
return searchRec(root.left, value);
}
// In-order traversal of the BST
void inOrderTraversal() {
inOrderRec(root);
}
// Recursive method for in-order traversal
void inOrderRec(Node root) {
if (root != null) {
inOrderRec(root.left);
System.out.print(root.value + " ");
inOrderRec(root.right);
}
}
// Main method to test the implementation
public static void main(String[] args) {
BinarySearchTree bst = new BinarySearchTree();
// Insert values into the BST
bst.insert(50);
bst.insert(30);
bst.insert(20);
bst.insert(40);
bst.insert(70);
bst.insert(60);
bst.insert(80);
29
// Perform in-order traversal
System.out.println("In-order traversal of the BST:");
bst.inOrderTraversal(); // Output: 20 30 40 50 60 70 80
// Search for a value
int key = 60;
System.out.println("\nIs " + key + " present in the BST? " + bst.search(key)); // Output:
true
}
}
