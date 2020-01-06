Editorial: 💡 Delete nodes from BST

Delete function is used to delete the specified node from a binary search tree. However, we must delete a node from a binary search tree in such a way, that the property of binary search tree doesn't violate. There are three situations of deleting a node from binary search tree.

1) The node to be deleted is a leaf node: It is the simplest case, in this case, replace the leaf node with the NULL and simple free the allocated space.

In the following image, we are deleting the node 85, since the node is a leaf node, therefore the node will be replaced with NULL and allocated space will be freed.  2) The node to be deleted has only one child: In this case, replace the node with its child and delete the child node, which now contains the value which is to be deleted. Simply replace it with the NULL and free the allocated space.

In the following image, the node 12 is to be deleted. It has only one child. The node will be replaced with its child node and the replaced node 12 (which is now leaf node) will simply be deleted.  3) The node to be deleted has two children: It is a bit complexed case compare to other two cases. However, the node which is to be deleted, is replaced with its in-order successor or predecessor recursively until the node value (to be deleted) is placed on the leaf of the tree. After the procedure, replace the node with NULL and free the allocated space.

In the following image, the node 50 is to be deleted which is the root node of the tree. The in-order traversal of the tree given below.

6, 25, 30, 50, 52, 60, 70, 75.

replace 50 with its in-order successor 52. Now, 50 will be moved to the leaf of the tree, which will simply be deleted. 

Code

     public class TreeNode {
      int val;
      TreeNode left;
      TreeNode right;
      TreeNode(int x) { val = x; }
  }

     public TreeNode deleteNode(TreeNode root, int key) {

        if(root == null){
            return root;
        }

     return delete(root,key);

    }

    public TreeNode max(TreeNode node){

        if(node.right != null){
            return max(node.right);
        }

        return node;
    }

   public TreeNode delete(TreeNode root, int key){

        if(root == null){
            return root;
        }

        if(root.val < key){
            root.right = delete(root.right, key);
        }else if(root.val > key){
            root.left = delete(root.left, key);
        }else{

            if(root.left == null){
                return root.right;
            }else if(root.right == null){
                return root.left;
            }


            TreeNode temp = max(root.left);
            root.val = temp.val;
            root.left = delete(root.left, root.val);


        }

        return root;
    }