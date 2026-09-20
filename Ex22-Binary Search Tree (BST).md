# Ex22 Searching for a Book ID in a Binary Search Tree (BST)

## DATE: 20/09/2026

## AIM:

To design and implement a Java program that constructs a Binary Search Tree (BST) using given Book IDs and checks whether a specific Book ID exists in the BST.

## Algorithm

1. Read the number of Book IDs and insert each ID into the Binary Search Tree.
2. For each Book ID, place smaller values in the left subtree and larger values in the right subtree.
3. Read the Book ID to be searched.
4. Compare the search value with the current node and move left or right accordingly.
5. If the value is found, print that the Book ID exists; otherwise, print that it does not exist.

## Program:

```java id="b3j6yu"
/*
Program to construct a Binary Search Tree (BST) using given Book IDs
Developed by: LAKSHMIDHAR N
RegisterNumber:  212224230138
*/

import java.util.*;

public class Main {

    static class Node {
        int data;
        Node left, right;

        Node(int data) {
            this.data = data;
        }
    }

    static Node insert(Node root, int data) {
        if (root == null)
            return new Node(data);

        if (data < root.data)
            root.left = insert(root.left, data);
        else if (data > root.data)
            root.right = insert(root.right, data);

        return root;
    }

    static boolean search(Node root, int key) {
        if (root == null)
            return false;

        if (root.data == key)
            return true;

        if (key < root.data)
            return search(root.left, key);

        return search(root.right, key);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        Node root = null;

        for (int i = 0; i < n; i++) {
            root = insert(root, sc.nextInt());
        }

        int key = sc.nextInt();

        if (search(root, key))
            System.out.println("Book ID exists");
        else
            System.out.println("Book ID does not exist");
    }
}
```

## Output:

<img width="397" height="162" alt="image" src="https://github.com/user-attachments/assets/6ff78b9b-75e0-403b-881c-3f41f883880e" />


## Result:

The program has been successfully implemented and executed.
It constructs a Binary Search Tree from the given Book IDs and accurately determines whether a queried Book ID exists in the library system.
