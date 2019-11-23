Editorial: 💡 Trees -- Find sum at level K

Here, the question says to find out if the sum of all the nodes present at a given level K.
We can reduce the problem into smaller subproblem by traversing the left subtree and right subtree and reducing k whenever we traverse a new level i.e reduce k by -1 at each level. Then we for every left and right subtree call we will check if we are at the correct level or not.
If k becomes zero at any point then we are at our desired level and we will return the data of the node from this level.
If the node is not present we will return 0 as the base case for the problem.

int sumAtLevelK(node *root, int k) {
    if(root==NULL) {
        return 0;
    }
    if(k<=0) {
        return root->data;
    }
    int leftAns = sumAtLevelK(root->left, k-1);
    int rightAns = sumAtLevelK(root->right, k-1);
    return leftAns+rightAns;
}