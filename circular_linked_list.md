Editorial: 💡 Circular Linked List
X
In this problem linked list is having a loop like this.

Change this linked list to 1-> 2 -> 3 -> 4-> 5 -> null.
We will use Floyd Cycle Detection algorithm to detect and remove the loop. In the Floyd’s algo, the slow and fast pointers meet at a loop node. We can use this loop node to remove cycle. There are following two different ways of removing loop when Floyd’s algorithm is used for Loop detection.

Method 1 (Check one by one):

We know that Floyd’s Cycle detection algorithm terminates when fast and slow pointers meet at a common point. We also know that this common point is one of the loop nodes (2 or 3 or 4 or 5 in the above diagram).
We store the address of this in a pointer variable say ptr2.
Then we start from the head of the Linked List and check for nodes one by one if they are reachable from ptr2.
When we find a node that is reachable, we know that this node is the starting node of the loop in Linked List and we can get pointer to the previous of this node.
Method 2 (Better Solution) :
This method is also dependent on Floyd’s Cycle detection algorithm.
1) Detect Loop using Floyd’s Cycle detection algo and get the pointer to a loop node.
2) Count the number of nodes in loop. Let the count be k.
3) Fix one pointer to the head and another to kth node from head.
4) Move both pointers at the same pace, they will meet at loop starting node.
5) Get pointer to the last node of loop and make next of it as NULL.

Code

public boolean detectRemoveLoop() {

        // detect loop
        Node slow = head;
        Node fast = head;

        while (fast != null && fast.next != null) {

            slow = slow.next;
            fast = fast.next.next;

            if (slow == fast)
                break;
        }

        if (slow == fast) {

            // loop remove
            Node start = head;
            Node loop = slow;

            while (start.next != loop.next) {
                start = start.next;
                loop = loop.next;
            }

            loop.next = null;

            return true;

        } else {

            // loop doesnot exist
            return false;
        }

    }
