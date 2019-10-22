Editorial: 💡 LL - k Reverse

The need of the question is to reverse every k nodes (where k is an input to the function) and k is a factor of size of List.

Example:

Inputs: 1->2->3->4->5->6->7->8->NULL and k = 3

Output: 3->2->1->6->5->4->8->7->NULL.

Algorithm :

Reverse the first sub-list of size k.

1.1 While reversing keep track of the next node and previous node.

1.2 Let the pointer to the next node be next and pointer to the previous node be prev.

head->next = reverse(next, k) /* Recursively call for rest of the list and link the two sub-lists */

return prev /* prev becomes the new head of the list (see the diagrams of iterative method of this post) */

Function Code


Node reverse(Node head, int k)
    { 

       Node current = head; 
       Node next = null; 
       Node prev = null; 

       int count = 0; 

       /* Reverse first k nodes of linked list */
       while (count < k && current != null)  
       { 
           next = current.next; 
           current.next = prev; 
           prev = current; 
           current = next; 
           count++; 
       } 

       /* next is now a pointer to (k+1)th node  
          Recursively call for the list starting from current. 
          And make rest of the list as next of first node */
       if (next != null)  
          head.next = reverse(next, k); 

       // prev is now head of input list 
       return prev; 
}