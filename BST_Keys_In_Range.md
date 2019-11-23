Editorial: 💡 Print BST keys in the given range
X
Algorithm:

1) If value of root’s key is greater than k1, then recursively call in left subtree.
2) If value of root’s key is in range, then print the root’s key.
3) If value of root’s key is smaller than k2, then recursively call in right subtree.


void Print(struct node *root, int k1, int k2)
{
/* base case */
if ( NULL == root )
    return;

/* Since the desired o/p is sorted, recurse for left subtree first
    If root->data is greater than k1, then only we can get o/p keys
    in left subtree */
if ( k1 < root->key )
    Print(root->left, k1, k2);

/* if root's data lies in range, then prints root's data */
if ( k1 <= root->key && k2 >= root->key )
    printf("%d ", root->key );

/* If root->data is smaller than k2, then only we can get o/p keys
    in right subtree */
if ( k2 > root->key )
    Print(root->right, k1, k2);
}
Lang - Java

public void printInRange(int lo, int hi) {
        printInRange(root, lo, hi);
    }

    private void printInRange(Node node, int lo, int hi) {

        if (node == null) {
            return;
        }

        if (node.data < lo) {
            printInRange(node.right, lo, hi);
        } else if (node.data > hi) {
            printInRange(node.left, lo, hi);
        } else {

            printInRange(node.left, lo, hi);
            System.out.println(node.data);
            printInRange(node.right, lo, hi);
        }
    }