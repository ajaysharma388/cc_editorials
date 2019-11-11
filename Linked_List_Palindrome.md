Editorial: 💡 Palindrome

Approach

The Idea is to Use Recursion to check whether the LinkedList is palindrome or not.
To check Palindrome we have used 2 Variable which points to the starting and end of the List.
As The Linked List is singly so we can go from one node to next node by moving frwd but we cannot move backwards in the LinkedList.
To move our pointing Variable backwards we are using Recursion.
To move our pointing variable frwd we are using a class which is Heapmover so that the incrementation could Exist on recursive stacks( Memory here ).
To check Palindrome we have Used a Headmover class so that the Starting pointer could increment and its update value could reflect on the recursive calls also.
Code

    private class heapmover {
        Node n1;
    }
    public boolean palindrome() {
        heapmover mover = new heapmover();
        mover.n1 = this.head;
        return palindrome(mover, this.head, 0);
    }
    public boolean palindrome(heapmover mover, Node n2, int cnt) {
        if (n2 == null) {
            return true;
        }
        boolean b = palindrome(mover, n2.next, cnt + 1);
        if (n2 != null && cnt > this.size / 2) {
            if (mover.n1.data != n2.data) {
                return false;
            }
        }
        mover.n1 = mover.n1.next;
        return b;
    }