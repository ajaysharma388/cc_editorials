Editorial: 💡 Tree bottom view

This problem can be easily solved with the help of Hashing. The idea is to create an empty map where each key represents the relative horizontal distance of the node from the root node and value in the map maintains a pair containing node’s value and its level number. Then we do a pre-order traversal of the tree and if current level of a node is more than or equal to maximum level seen so far for the same horizontal distance as current node’s or current horizontal distance is seen for the first time, we update the value and the level for current horizontal distance in the map. For each node, we recurse for its left subtree by decreasing horizontal distance and increasing level by 1 and recurse for right subtree by increasing both level and horizontal distance by 1. tree
tree


void bottomViewHelper(node *root, int level, int dist, map<int, pair<int, int> > &mp) {
    if(root == NULL) {
        return;
    }
    if(mp.find(dist) == mp.end() or level>=mp[dist].second) {
        mp[dist] = {root->data, level};
    }
    bottomViewHelper(root->left, level+1, dist-1, mp);
    bottomViewHelper(root->right, level+1, dist+1, mp);
}
void bottomView(node *root)
{
   map<int, pair<int, int> >mp;
   bottomViewHelper(root, 0, 0, mp);
   for(auto val:mp){
       cout<<val.second.first<<" ";
   }
}
Lang - Java

public  void bottomView() {

        HashMap map = new HashMap<>();
        dfs(root, 0, 0, map);
        ArrayList keys = new ArrayList<>(map.keySet());
        Collections.sort(keys);

        for (int key : keys) {
            System.out.print(map.get(key).data + " ");
        }

    // display(root);

    }

    public  void dfs(Node root, int vlevel, int ht, HashMap map) {

        if (root == null) {
            return;
        }


        if (!map.containsKey(vlevel)) {
            Pair np = new Pair();
            np.data = root.data;
            np.ht = ht;
            map.put(vlevel, np);
        } else {

             if (map.get(vlevel).ht <= ht) {
                map.get(vlevel).ht = ht;
                map.get(vlevel).data = root.data;
            }
        }

        dfs(root.left, vlevel - 1, ht + 1, map);
        dfs(root.right, vlevel + 1, ht + 1,  map);
    }

     class Pair {

        int ht;
        int data;
    }