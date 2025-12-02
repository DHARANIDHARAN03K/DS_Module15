# Ex3(E) Largest Element in BST
## DATE:06-09-2025
## AIM:
To write a **Java program** to implement a **Binary Search Tree (BST)** and find the **largest value** present in the tree using an iterative approach.

## Algorithm:
1.  Start.
2.  Define a class `Node` with an integer `info` and `Node left, right` pointers.
3.  Define a class `BinarySearchTree` to manage the root and insertion logic.
4.  Define the **`findLargest(Node root)`** method:
    a. Check if the `root` is null; if so, return an appropriate value (e.g., -1) or throw an exception.
    b. Initialize a temporary node pointer, say `current`, to the `root`.
    c. **Iteratively** move the `current` pointer to its **right child** in a loop (while `current.right` is not null). 
    d. The loop stops when `current` is the rightmost node.
    e. Return the `info` of the `current` node as the largest value.
5.  In the `main` method, construct a sample BST and call `findLargest()` to display the result.
6.  End.

## Program:
/*
Program to find the largest value in a Binary Search Tree
Developed by: Dharani dharan K
RegisterNumber: 212223040036
*/

class Node {
    int info;
    Node left, right;

    public Node(int key) {
        info = key;
        left = right = null;
    }
}

public class BinarySearchTree {
    Node root;

    public BinarySearchTree() {
        root = null;
    }

    // Utility function to insert a new node
    public Node insert(Node node, int key) {
        if (node == null) {
            return new Node(key);
        }
        if (key < node.info) {
            node.left = insert(node.left, key);
        } else if (key > node.info) {
            node.right = insert(node.right, key);
        }
        return node;
    }

    // Function to find the largest element
    public int findLargest(Node node) {
        if (node == null) {
            System.out.println("Tree is empty.");
            return -1; 
        }

        Node current = node;
        // The largest element is the rightmost node in a BST
        while (current.right != null) {
            current = current.right;
        }
        return current.info;
    }

    // Utility function for Inorder traversal
    void inorder(Node root) {
        if (root != null) {
            inorder(root.left);
            System.out.print(root.info + " ");
            inorder(root.right);
        }
    }

    public static void main(String[] args) {
        BinarySearchTree tree = new BinarySearchTree();

        // Building the sample tree (matching the C code's structure)
        tree.root = tree.insert(tree.root, 25);
        tree.root = tree.insert(tree.root, 17);
        tree.root = tree.insert(tree.root, 35);
        tree.root = tree.insert(tree.root, 13);
        tree.root = tree.insert(tree.root, 19);
        tree.root = tree.insert(tree.root, 27);
        tree.root = tree.insert(tree.root, 55);
        
        System.out.print("Inorder traversal of tree: ");
        tree.inorder(tree.root);
        System.out.println();
        
        int largestValue = tree.findLargest(tree.root);
        
        System.out.println("\nLargest value is " + largestValue);
    }
}

## Output:
![image](https://github.com/user-attachments/assets/23cf1270-fdba-4c49-ae95-3c2c5f339d3a)
## Result:
Thus, the **Java program** to find the largest value in a Binary Search Tree is implemented successfully.
