Editorial: 💡 Level Order ( Zigzag

We will be using 2 stacks to solve this problem. One for the current layer and other one for the next layer. Also keep a flag which indicates the direction of traversal on any level.

You need to pop out the elements from current layer stack and depending upon the value of flag push the childs of current element in next layer stack. You should maintain the output sequence in the process as well. Remember to swap the stacks before next iteration.

Lang - Cpp

void levelOrderZigZag(node *root) {
    stack<node *> s1;
    stack<node *> s2;
    bool leftOrRight = true;
    s1.push(root);
    while(!s1.empty() or !s2.empty()) {
        int row = 0;
        if(s1.size() > s2.size()) {
            row = s1.size();
        } else {
            row = s2.size();
        }
        while(row--) {
            if(leftOrRight) {
                node *curr = s1.top();
                s1.pop();
                cout<<curr->data<<" ";
                if(curr->left)
                    s2.push(curr->left);
                if(curr->right)
                    s2.push(curr->right);
            } else {
                node *curr = s2.top();
                s2.pop();
                cout<<curr->data<<" ";
                if(curr->right)
                    s1.push(curr->right);
                if(curr->left)
                    s1.push(curr->left);
            }
        }
        leftOrRight = !leftOrRight;
    }
}
Lang - Java

public void levelOrderZZ() {

        LinkedList list = new LinkedList<>();
        LinkedList stack = new LinkedList<>();
        list.addLast(this.root);

        int count = 0;

        while (!list.isEmpty()) {
            Node rn = list.removeFirst();

            if (rn != null) {
                System.out.print(rn.data + " ");

                if (count % 2 == 0) {

                    stack.addFirst(rn.left);
                    stack.addFirst(rn.right);

                } else

                {
                    stack.addFirst(rn.right);
                    stack.addFirst(rn.left);

                }
            }
            if (list.isEmpty()) {
                // System.out.println();
                list = stack;
                stack = new LinkedList<>();
                count++;
            }

        }
    }