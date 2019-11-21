Editorial: 💡 Structurally Identical (Binary Tree)

Here, the question says to find out if the two given binary trees are structurally identical or not.
Algorithm:

Here the smaller problem is to find out whether the left subtree and right subtree of the root node for the two trees are structurally similar or not.
If true, return true. Else even if one the condition is false, return false.
There will be two base cases for the given question.
a) If both the trees are empty, return true.
b) If one of the trees remain null and other one does not, then return false.
Lang - Cpp

int areTreesStructurallyIdentical(node *root1, node *root2) {
    if(root1==NULL and root2==NULL) {
        return 1;
    }
    if(root1!=NULL and root2!=NULL) {
        int leftAns = areTreesStructurallyIdentical(root1->left, root2->left);
        int rightAns = areTreesStructurallyIdentical(root1->right, root2->right);
        return leftAns and rightAns;
    }
    return 0;
}
Lang - Java

private boolean structurallyIdentical(Node tnode, Node onode) {

        if (tnode == null && onode == null)
            return true;
        if (size(tnode) != size(onode))
            return false;

        boolean rr = structurallyIdentical(tnode.left, onode.left);
        if (!rr)
            return false;
        rr = structurallyIdentical(tnode.right, onode.right);
        if (!rr)
            return false;

        return true;

    }