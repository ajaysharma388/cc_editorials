Editorial: 💡 Tree top view

 The idea is to create an empty map where each key represents the relative horizontal distance of the node from the root node and value in the map maintains a pair containing node’s value and its level number. Then we do a pre-order traversal of the tree and if current level of a node is less than maximum level seen so far for the same horizontal distance as current node’s or current horizontal distance is seen for the first time, we update the value and the level for current horizontal distance in the map. For each node, we recurse for its left subtree by decreasing horizontal distance and increasing level by 1 and recurse for right subtree by increasing both level and horizontal distance by 1.
tree
tree


void topView1(node *root, int level, int dist, map<int, pair<int, int> > &mp) {
    if(root == NULL) {
        return;
    }
    if(mp.find(dist) == mp.end() or level<mp[dist].second) {
        mp[dist] = {root->data, level};
    }
    topView1(root->left, level+1, dist-1, mp);
    topView1(root->right, level+1, dist+1, mp);
}
void topView(node *root)
{
   map<int, pair<int, int> >mp;
   topView1(root, 0, 0, mp);
   for(auto val:mp){
       cout<<val.second.first<<" ";
   }
}
Another approach can be using a queue.

The idea here is to observe that, if we try to see a tree from its top, then only the nodes which are at top in vertical order will be seen.
Start BFS from root. Maintain a queue of pairs comprising of node(Node *) type and vertical distance of node from root. Also, maintain a map which should store the node at a particular horizontal distance.
While processing a node, just check if any node is there in the map at that vertical distance.
If any node is there, it means the node can’t be seen from top, do not consider it. Else, if there is no node at that vertical distance, store that in map and consider for top view.

void topViewIterative(node *root) {
    queue<pair<node *, int>> qu;
    qu.push({root, 0});
    map<int, int>mp;
    while(!qu.empty()) {
        node* temp = qu.front().first;
        int dist = qu.front().second;
        qu.pop();
        if(mp.find(dist) == mp.end()) {
            cout<<temp->data<<" ";
            mp[dist] = temp->data;
        }
        if(temp->left) {
            qu.push({temp->left, dist-1});
        }
        if(temp->right) {
            qu.push({temp->right, dist+1});
        }
    }
}
Lang - Java

 public  void TopView() {

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

            //     System.out.println(root.data+" h:"+ht);

            if (map.get(vlevel).ht > ht) {
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