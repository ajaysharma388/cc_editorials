Editorial: 💡 Replace with Sum of greater nodes

We can do it using a single traversal. The idea is to use following BST property. If we do reverse Inorder traversal of BST, we get all nodes in decreasing order. We do reverse Inorder traversal and keep track of the sum of all nodes visited so far, we add this sum to every node.


import java.util.*;

public class Main {
    private class Node {
        int data;
        Node left;
        Node right;

        Node(int data, Node left, Node right) {
            this.data = data;
            this.left = left;
            this.right = right;
        }
    }

    private Node root;
    private int size;

    public Main(int... sa) {
        this.root = this.construct(sa, 0, sa.length - 1);
    }

    private Node construct(int[] sa, int lo, int hi) {
        if (lo > hi) {
            return null;
        }
        int mid = (lo + hi) / 2;
        Node rv = new Node(sa[mid], null, null);
        this.size++;
        rv.left = this.construct(sa, lo, mid - 1);
        rv.right = this.construct(sa, mid + 1, hi);
        return rv;
    }

    public void modifyBST() {
        int[] arr = {0};
        this.modifyBSTwithgreaterelementssum(this.root, arr);
    }

    private void modifyBSTwithgreaterelementssum(Node node, int[] sum) {
        if(node == null)
            return;
        modifyBSTwithgreaterelementssum(node.right, sum);
        sum[0]+=node.data;
        node.data = sum[0];
        modifyBSTwithgreaterelementssum(node.left, sum);
    }

    public void preorder() {
        pre_order(this.root);
    }

    private void pre_order(Node node) {
        if(node ==null) return;
        System.out.print(node.data+" ");
        pre_order(node.left);
        pre_order(node.right);

    }

    public static void main(String[] args) {
        Scanner scn = new Scanner(System.in);
        int n = scn.nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = scn.nextInt();
        }

        Main b = new Main(arr);
        b.modifyBST();
        b.preorder();
    }

}