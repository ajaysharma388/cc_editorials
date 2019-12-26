Editorial: 💡 Importance of Time

Approach

The Idea is to Store the Calling order in Queue and the ideal order in an Array.
Then compare front element of the queue with the ideal order.
If it matches then increment the time and remove the element.
Else, Dequeue the element and enqueue it again.
The loop will run till the queue is consumed totally.
code

  public static void func(LinkedList q,int n,int[] arr)throws Exception{
        int ans = 0;
        for(int j = 0;j<n;j++) {
            if(q.getFirst() == arr[j]) {
                ans++;
                q.removeFirst();
            }else {
                while(q.getFirst() != arr[j]) {
                int var = q.getFirst();
                q.addLast(var);
                q.removeFirst();
                ans++;
                }
                ans++;
                q.removeFirst();
            }

    }
    System.out.println(ans);

}