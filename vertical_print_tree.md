Editorial: 💡 Vertical Order Print Binary Tree
X
Approach
We can do preorder traversal of the given Binary Tree. While traversing the tree, we can recursively calculate HDs. We initially pass the horizontal distance as 0 for root. For left subtree, we pass the Horizontal Distance as Horizontal distance of root minus 1. For right subtree, we pass the Horizontal Distance as Horizontal Distance of root plus 1. For every HD value, we maintain a list of nodes in a hash map. Whenever we see a node in traversal, we go to the hash map entry and add the node to the hash map using HD as a key in map.

Figure

Code

private class VOPair {
        int data;
        int vl;
        int hl;

        @Override
        public String toString() {
            return this.data + "";
        }
    }

    public void verticalOrder() {

        HashMap> map = new HashMap<>();

        verticalOrder(root, 0, 0, map);

        ArrayList keys = new ArrayList<>(map.keySet());

        Collections.sort(keys); // [-2,-1,0,1,2]

        for (int key : keys) {
            ArrayList list = map.get(key);

            Collections.sort(list, new VOComparator());
            System.out.println(key + " -> " + list);
        }

        // System.out.println(map);

    }

    private class VOComparator implements Comparator {

        @Override
        public int compare(VOPair o1, VOPair o2) {
            return o1.hl - o2.hl;
        }

    }

    private void verticalOrder(Node node, int vLevel, int hLevel, HashMap> map) {

        if (node == null) {
            return;
        }

        if (!map.containsKey(vLevel)) {
            map.put(vLevel, new ArrayList<>());
        }

        VOPair np = new VOPair();
        np.data = node.data;
        np.hl = hLevel;
        np.vl = vLevel;
        map.get(vLevel).add(np);

        verticalOrder(node.left, vLevel - 1, hLevel + 1, map);
        verticalOrder(node.right, vLevel + 1, hLevel + 1, map);

    }