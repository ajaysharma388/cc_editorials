Editorial: 💡 Tree Left View

The problem can also be solved using simple recursive traversal. We can keep track of level of a node by passing a parameter to all recursive calls. The idea is to keep track of maximum level also. Whenever we see a node whose level is more than maximum level so far, we print the node because this is the first node in its level (Note that we traverse the left subtree before right subtree).


void leftViewHelper(node *root, int level, int &max_level) {
    if(root == NULL) {
        return;
    }
    if(max_level<level) {
        cout<<root->data<<" ";
        max_level = level;
    }
    leftViewHelper(root->left, level+1, max_level);
    leftViewHelper(root->right, level+1, max_level);
}

void leftView(node *root) {
    int max_level = 0;
    leftViewHelper(root, 1, max_level);
}
Lang - Java

 public  void LeftView() {

        int[] maxLevel = new int[1];
        maxLevel[0] = -1;
        dfs(root, 0, maxLevel);

    }

    public  void dfs(Node root, int level, int[] maxLevel) {

        if (root == null) {
            return;
        }


        if(level > maxLevel[0]){
            System.out.print(root.data+" ");
            maxLevel[0] = level;
        }

        dfs(root.left, level + 1, maxLevel);
        dfs(root.right, level + 1, maxLevel);
    }