# Ex21 Count the Number of Nodes in the Left Subtree of a Binary Tree

## DATE: 20/09/2026

## AIM:

To design and implement a Java program that constructs a binary tree from given level order input and counts the number of nodes present in the left subtree of the root node.

## Algorithm

1. Read the number of nodes and store the level order values in an array.
2. Construct the binary tree using the level order values.
3. Access the left subtree of the root node.
4. Recursively count all the nodes present in the left subtree.
5. Display the total number of nodes in the left subtree.

## Program:

```java id="0t7m2k"
/*
Program to construct a binary tree from given level order input and count the number of nodes
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

    static Node buildTree(int[] arr) {
        if (arr.length == 0)
            return null;

        Node[] nodes = new Node[arr.length];

        for (int i = 0; i < arr.length; i++)
            nodes[i] = new Node(arr[i]);

        for (int i = 0; i < arr.length; i++) {
            int left = 2 * i + 1;
            int right = 2 * i + 2;

            if (left < arr.length)
                nodes[i].left = nodes[left];

            if (right < arr.length)
                nodes[i].right = nodes[right];
        }

        return nodes[0];
    }

    static int countNodes(Node root) {
        if (root == null)
            return 0;

        return 1 + countNodes(root.left) + countNodes(root.right);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] arr = new int[n];

        for (int i = 0; i < n; i++)
            arr[i] = sc.nextInt();

        Node root = buildTree(arr);

        int count = countNodes(root.left);

        System.out.println(count);
    }
}
```

## Output:

<img width="382" height="137" alt="image" src="https://github.com/user-attachments/assets/3b574609-a156-4bfb-8bed-f851910cf36e" />


## Result:

The program has been successfully implemented and executed.
It correctly constructs the binary tree from level order input and counts the number of nodes in the left subtree of the root node.
