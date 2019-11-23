Editorial: 💡 Build BST

Get the Middle of the array and make it root.
Recursively do same for left half and right half.
a) Get the middle of left half and make it left child of the root created in step 1.
b) Get the middle of right half and make it right child of the root created in step 1.

#include<stdio.h>
#include<stdlib.h>

/* A Binary Tree node */
struct TNode
{
    int data;
    struct TNode* left;
    struct TNode* right;
};

struct TNode* newNode(int data);

/* A function that constructs Balanced Binary Search Tree from a sorted array */
struct TNode* sortedArrayToBST(int arr[], int start, int end)
{
    /* Base Case */
    if (start > end)
    return NULL;

    /* Get the middle element and make it root */
    int mid = (start + end)/2;
    struct TNode *root = newNode(arr[mid]);

    /* Recursively construct the left subtree and make it
    left child of root */
    root->left = sortedArrayToBST(arr, start, mid-1);

    /* Recursively construct the right subtree and make it
    right child of root */
    root->right = sortedArrayToBST(arr, mid+1, end);

    return root;
}

/* Helper function that allocates a new node with the
given data and NULL left and right pointers. */
struct TNode* newNode(int data)
{
    struct TNode* node = (struct TNode*)
                        malloc(sizeof(struct TNode));
    node->data = data;
    node->left = NULL;
    node->right = NULL;

    return node;
}

/* A utility function to print preorder traversal of BST */
void preOrder(struct TNode* node)
{
    if (node == NULL)
        return;
    printf("%d ", node->data);
    preOrder(node->left);
    preOrder(node->right);
}

/* Driver program to test above functions */
int main()
{
    int t;
    scanf("%d", &t);
    for(int i=0;i<t;i++)
    {
        int n;
        scanf("%d", &n);
        int arr[n];
        for(int j=0;j<n;j++)
        scanf("%d", &arr[j]);
        struct TNode *root = sortedArrayToBST(arr, 0, n-1);
    //printf("n PreOrder Traversal of constructed BST ");
    preOrder(root);
    printf("\n");

    }
    /*int arr[] = {1, 2, 3, 4, 5, 6, 7};
    int n = sizeof(arr)/sizeof(arr[0]);


    struct TNode *root = sortedArrayToBST(arr, 0, n-1);
    printf("n PreOrder Traversal of constructed BST ");
    preOrder(root);*/

    return 0;
}

Lang - Java

import java.util.*;
public class BST {

    private class Node {
        int data;
        Node left;
        Node right;
    }

    private Node root;

    public BST(int[] in) {
        this.root = construct(in, 0, in.length - 1);
    }

    private Node construct(int[] in, int lo, int hi) {

        if (lo > hi) {
            return null;
        }

        int mid = (lo + hi) / 2;

        Node nn = new Node();
        nn.data = in[mid];

        nn.left = construct(in, lo, mid - 1);
        nn.right = construct(in, mid + 1, hi);

        return nn;

    }

    public void display(){
        display(this.root);
    }

    public void display(Node root) {

        if(root == null) return;

        System.out.print(root.data+" ");
        display(root.left);
        display(root.right);

    }

 public static void main(String[] args){

         int t = scn.nextInt();

        while(t-- > 0){
             int[] inorder = takeinput();
             BST tree = new BST(inorder);
             tree.display();
        }

 }

 static Scanner scn = new Scanner(System.in);

 public static int[] takeinput() {

        int n = scn.nextInt();
        int[] array = new int[n];

        for (int i = 0; i < array.length; i++) {
            array[i] = scn.nextInt();
        }

        return array;
    }
}