# Ex3(A) Tree Representation and Traversal
## DATE:06-09-2025
## AIM:
To write a **Java program** to implement a Binary Tree and demonstrate the **Post-order Traversal** technique.

## Algorithm:
1.  Start.
2.  Define a class `Node` to represent the tree structure, containing an integer `data` and pointers to the `left` and `right` children (`Node left, right`).
3.  Define a class `BinaryTree` to manage the root of the tree and traversal methods.
4.  Define the **`postOrder(Node node)`** method:
    a. Check if the current `node` is **not null**.
    b. Recursively call `postOrder()` for the **left child** (`node.left`).
    c. Recursively call `postOrder()` for the **right child** (`node.right`).
    d. **Visit** and print the `data` of the current `node`.
5.  In the `main` method, create an instance of the `BinaryTree` and build a sample tree structure.
6.  Call the `postOrder()` method starting from the root to display the traversal sequence.
7.  End.


## Program:
/*
Program to perform post order traversal of a binary tree.
Developed by: Dharani dharan K
RegisterNumber: 212223040036
*/

class Node {
    int data;
    Node left, right;

    public Node(int item) {
        data = item;
        left = right = null;
    }
}

public class BinaryTree {
    Node root;

    public BinaryTree() {
        root = null;
    }
    
    // Function to perform Post-order Traversal (Left -> Right -> Root)
    public void postOrder(Node node) {
        if (node == null)
            return;

        // 1. Traverse the left subtree
        postOrder(node.left);

        // 2. Traverse the right subtree
        postOrder(node.right);

        // 3. Visit the root node
        System.out.print(node.data + " ");
    }

    public static void main(String[] args) {
        BinaryTree tree = new BinaryTree();

        // Building a sample tree:
        //       1
        //      / \
        //     2   3
        //    / \
        //   4   5
        tree.root = new Node(1);
        tree.root.left = new Node(2);
        tree.root.right = new Node(3);
        tree.root.left.left = new Node(4);
        tree.root.left.right = new Node(5);

        System.out.println("--- Binary Tree Post-order Traversal ---");
        System.out.print("Post-order Traversal: ");
        tree.postOrder(tree.root);
        System.out.println();
    }
}

## Output:
![image](https://github.com/user-attachments/assets/23cf1270-fdba-4c49-ae95-3c2c5f339d3a)
## Result:
Thus, the **Java program** to implement a Binary Tree and perform post-order traversal is implemented successfully.
