Editorial: 💡 Dequeue efficient queue using stack
X
Approach
To make QueueUsingStack to be Dequeue efficient all you need to do is to maintain the order at the time of Enqueue in the queue so that at the time of Dequeue you are able to remove the topmost element.

Enqueue Function
To maintain the order of the elements in the stack all you need to do is to first remove all of the elements and save them in another stack then Enqueue the new element in the bottom of the stack and then again Enqueue the previusly removed elements.

Dequeue Function
This function will become efficient as the topmost element in the stack is the firstly added element.

Code

public class QueueUsingStackDeqEff {

    DynamicStack s = new DynamicStack();

    public void enqueue(int item) throws Exception {

        try {
            DynamicStack helper = new DynamicStack();

            while (!s.isEmpty()) {
                helper.push(s.pop());
            }

            s.push(item);

            while (!helper.isEmpty()) {
                s.push(helper.pop());
            }

        } catch (Exception e) {
            throw new Exception("Queue is Full.");
        }
    }

    public int dequeue() throws Exception {

        try {
            return s.pop();
        } catch (Exception e) {
            throw new Exception("Queue is Empty");
        }
    }

    public int getFront() throws Exception {

        try {
            return s.peek();
        } catch (Exception e) {
            throw new Exception("Queue is Empty");
        }
    }

    public int size() {

        return s.size();
    }

    public boolean isEmpty() {
        return s.isEmpty();
    }

    public boolean isFull() {
        return s.isFull();
    }

    public void display() {

        s.display();

    }
}