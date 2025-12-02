# Ex3(C) Expression Tree
## DATE:06-09-2025
## AIM:
To write a **Java program** to construct an **Expression Tree** from a given **Postfix Expression** and display the tree contents using **In-order**, **Pre-order**, and **Post-order** traversals.

## Algorithm:
1.  Start.
2.  Define a `Node` class with a `char data` field (for operator/operand) and `Node left, right` pointers.
3.  Define the **`isOperator(char c)`** function to check if a character is an operator (+, -, *, /).
4.  Define the **`constructTree(String postfix)`** method using a **Stack of Nodes**:
    a. Traverse the input `postfix` expression character by character.
    b. **If the character is an operand**, create a new `Node` and push it onto the stack. 
    c. **If the character is an operator**, create a new `Node` for the operator.
        i. Pop the top two nodes from the stack; these will be the right child ($T_2$) and the left child ($T_1$) of the new operator node, respectively.
        ii. Set the new operator node's children: $operatorNode.left = T_1$ and $operatorNode.right = T_2$.
        iii. Push the new operator node onto the stack.
    d. After processing the entire expression, the single remaining node on the stack is the **root** of the Expression Tree.
5.  Define the recursive **`inOrder()`**, **`preOrder()`**, and **`postOrder()`** traversal methods.
6.  In the `main` method, pass a sample postfix expression to `constructTree()` and then call the three traversal methods on the resulting root node.
7.  End.

## Program:
/*
Program to construct an Expression Tree for the given Postfix Expression and display the output in the format of In-order, Pre-order and Post-order traversal.
Developed by: Dharani dharan K
RegisterNumber: 212223040036
*/

import java.util.Stack;

class Node {
    char data;
    Node left, right;

    public Node(char item) {
        data = item;
        left = right = null;
    }
}

public class ExpressionTree {
    
    // Check if the character is an operator
    static boolean isOperator(char c) {
        return c == '+' || c == '-' || c == '*' || c == '/';
    }

    // Function to construct the Expression Tree from a postfix expression
    static Node constructTree(String postfix) {
        Stack<Node> s = new Stack<>();
        Node t1, t2, temp;

        for (int i = 0; i < postfix.length(); i++) {
            char c = postfix.charAt(i);

            // If operand, push to stack
            if (!isOperator(c)) {
                temp = new Node(c);
                s.push(temp);
            } 
            // If operator, create internal node
            else {
                temp = new Node(c);

                // Pop two operands (T2 is the top, T1 is next)
                t2 = s.pop(); 
                t1 = s.pop();

                // Make T1 the left child and T2 the right child
                temp.left = t1;
                temp.right = t2;

                // Push the new subtree root back to the stack
                s.push(temp);
            }
        }
        // The root of the tree is the last element remaining in the stack
        return s.pop();
    }
    
    // Pre-order Traversal (Root, Left, Right)
    static void preOrder(Node tree) {
        if (tree != null) {
            System.out.print(tree.data + " ");
            preOrder(tree.left);
            preOrder(tree.right);
        }
    }

    // In-order Traversal (Left, Root, Right) - Gives infix expression with minimal parentheses
    static void inOrder(Node tree) {
        if (tree != null) {
            inOrder(tree.left);
            System.out.print(tree.data + " ");
            inOrder(tree.right);
        }
    }

    // Post-order Traversal (Left, Right, Root) - Gives back the original postfix expression
    static void postOrder(Node tree) {
        if (tree != null) {
            postOrder(tree.left);
            postOrder(tree.right);
            System.out.print(tree.data + " ");
        }
    }

    public static void main(String[] args) {
        String postfix = "ab*c+de*-";
        System.out.println("Input Postfix Expression: " + postfix);
        
        Node root = constructTree(postfix);
        
        System.out.println("\n--- Expression Tree Traversal Results ---");
        
        System.out.print("Pre-order (Prefix): ");
        preOrder(root);
        System.out.println();

        System.out.print("In-order (Infix): ");
        inOrder(root);
        System.out.println();

        System.out.print("Post-order (Postfix): ");
        postOrder(root);
        System.out.println();
    }
}

## Output:


![image](https://github.com/user-attachments/assets/23cf1270-fdba-4c49-ae95-3c2c5f339d3a)
## Result:
Thus, the **Java program** to construct an Expression Tree from a Postfix Expression and display the output using In-order, Pre-order, and Post-order traversal is implemented successfully.
