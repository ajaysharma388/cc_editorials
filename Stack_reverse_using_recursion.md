Editorial: 💡 REVERSE A STACK USING RECURSION

Algo.
First Empty your stack into another helper Stack.
Then Using Recursion copy element from helper to stack.
Till the Stack is reversed.
Code

    public void reverseStack(StacksUsingArrays s, StacksUsingArrays h) throws Exception {

            if (s.isEmpty()) {

            if (h.isEmpty()) {
                return;
            }

            int val = h.pop();
            reverseStack(s, h);
            s.push(val);

            return;
        }

        int temp = s.pop();
        h.push(temp);

        reverseStack(s, h);
        }