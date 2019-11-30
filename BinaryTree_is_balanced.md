Editorial: 💡 Is_Balanced ( Binary Tree )

The question says to find out whether a given binary tree is balanced or not. A non-empty binary tree T is balanced if:
1) Left subtree of T is balanced
2) Right subtree of T is balanced
3) The difference between heights of left subtree and right subtree is not more than 1.
Also, an empty tree is balanced.
There are two ways to solve this problem.
Algorithm:

Get the height of left and right subtrees.
Return true if difference between heights is not more than 1 and left and right subtrees are balanced, otherwise return false.
Above implementation can be optimized by calculating the height in the same recursion rather than calling a height() function separately.
Algorithm:

Make a balancedPair which stores information about both the height of a node and whether its balanced or not.
Recursively compute the height and isbalanced property for both the left and right subtree.
Check if a particular node satisfies the balancing conditions or not.
If all the conditions are satisfied, the isbalanced value for the particular node is true. Else false.

 
pair< int, bool> isBalanced(node*root){
    pair < int ,bool > p,left,right;

    if(root==NULL){
        p.first = 0;
        p.second = true;
        return p;
    }

    //Rec Case
    left = isBalanced(root->left);
    right = isBalanced(root->right);

    int h = max(left.first,right.first) + 1;

    if(abs(left.first-right.first)<=1 and left.second and right.second){
        return make_pair(h,true);
    }
    return make_pair(h,false);

}
Lang - Java


        public boolean isBalanced() {
            return this.isBalanced(this.root).isBalanced;
        }

        private pair isBalanced(Node node) {

        if (node == null) {
            pair bd = new pair();
            bd.isBalanced = true;
            bd.height = -1;
            return bd;
        }

        pair sp = new pair();

        pair lib = isBalanced(node.left);
        pair rib = isBalanced(node.right);

        sp.height = Math.max(lib.height, rib.height) + 1;
        int bf = lib.height - rib.height;

        if (lib.isBalanced && rib.isBalanced && bf >= -1 && bf <= 1) {
            sp.isBalanced = true;
        } else
            sp.isBalanced = false;

        return sp;
        }

        private class pair {
            int height;
            boolean isBalanced;
        }