# Ex3(B) Binary Search Tree
## DATE:06-09-2025
## AIM:
To write a **Java program** to implement a **Binary Search Tree (BST)** and demonstrate the recursive function for inserting elements while maintaining the BST property.

## Algorithm:
1.  Start.
2.  Define a class `Node` to represent the tree structure, containing an integer `key` and pointers to the `left` and `right` children (`Node left, right`).
3.  Define the recursive **`insert(Node node, int key)`** method:
    a. **Base Case:** If the current `node` is `null`, create a new `Node` with the given `key`, and return it. 
    b. **Recursive Step:** If the `node` is not `null`, compare the `key` with `node.key`.
    c. If $key < node.key$, recursively call `insert()` for the **left subtree** and set `node.left` to the result.
    d. If $key \geq node.key$, recursively call `insert()` for the **right subtree** and set `node.right` to the result.
    e. Return the original `node` pointer.
4.  In the `main` method, create a BST instance and call the `insert()` function multiple times to build the tree.
5.  Perform a tree traversal (e.g., Inorder) to verify the BST structure and insertion.
6.  End.

## Program:
/*
Program to insert the elements in the binary search tree
Developed by: Dharani dharan K
RegisterNumber: 212223040036
*/

class Node {
    int key;
    Node left, right;

    public Node(int item) {
        key = item;
        left = right = null;
    }
}

public class BinarySearchTree {
    Node root;

    public BinarySearchTree() {
        root = null;
    }

    // A utility function to call the recursive insert
    public void insert(int key) {
        root = insertRec(root, key);
    }
    
    // The core recursive insertion function
    public Node insertRec(Node node, int key) {
        // Base Case: If the tree is empty, return a new node
        if (node == null) {
            System.out.println("Inserted: " + key);
            return new Node(key);
        }

        /* Otherwise, recur down the tree */
        if (key < node.key) {
            node.left = insertRec(node.left, key);
        } else if (key >= node.key) { // Using >= to handle duplicates/right insertion
            node.right = insertRec(node.right, key);
        }

        /* return the (unchanged) node pointer */
        return node;
    }

    // Utility function for Inorder traversal to verify the BST
    void inorderRec(Node root) {
        if (root != null) {
            inorderRec(root.left);
            System.out.print(root.key + " ");
            inorderRec(root.right);
        }
    }

    public static void main(String[] args) {
        BinarySearchTree tree = new BinarySearchTree();

        System.out.println("--- Inserting Elements into BST ---");
        tree.insert(50);
        tree.insert(30);
        tree.insert(70);
        tree.insert(20);
        tree.insert(40);
        tree.insert(60);
        tree.insert(80);

        System.out.println("\n--- BST Traversal Verification ---");
        System.out.print("Inorder Traversal (Should be sorted): ");
        tree.inorderRec(tree.root);
        System.out.println();
    }
}

## Output:
![image](https://github.com/user-attachments/assets/23cf1270-fdba-4c49-ae95-3c2c5f339d3a)
## Result:
Thus, the **Java program** to insert elements into a Binary Search Tree (BST) using a recursive function is implemented successfully.
