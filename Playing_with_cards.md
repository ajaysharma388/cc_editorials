Editorial: 💡 Playing with cards (In stack)

In this question we will use three stacks at a time. Stack1 is for storing the given cards.

For a particular ith iteration stack2 stores that cards which are divisible by ith prime number and rest of the cards are stored in stack3.

For the next iteration stack3 is now stack 1 and same steps are repeated.

Here Prime is the array of prime numbers.

For every iteration print the cards in stack2 and after the queries are over print the cards in stack1.

Lang - Cpp
Function:

void printCards(int[] primes ,int n,int q,stack 1)
{
    stack<int>  stack2, stack3;
    for(int i = 0 ; i < q; i++)
    {
        if(stack1.empty())
            break;
       // ith prime number from the prime array
        int cur = primes[i];
        while(!stack1.empty())
        {
            int ele = stack1.top();
            stack1.pop();
            if(ele%cur == 0)
            {
                stack2.push(ele);
            }
            else
            {
                stack3.push(ele);
            }
        }
        while(!stack2.empty())
        {
            cout<<stack2.top()<<endl;
            stack2.pop();
        }
        stack1 = stack3;
        while(!stack3.empty())
            stack3.pop();
    }
    while(!stack1.empty())
    {
        cout<<stack1.top()<<endl;
        stack1.pop();
    }
}
Lang - Java

public class PlayingCards {

    public static void main(String[] args) {

        Scanner scn = new Scanner(System.in);

        int noc = scn.nextInt();
        int q = scn.nextInt();

        ArrayList> A = new ArrayList<>();
        ArrayList> B = new ArrayList<>();

        for (int i = 1; i <= q + 1; i++) {
            A.add(new Stack<>());
            B.add(new Stack<>());
        }

        for (int i = 1; i <= noc; i++) {
            A.get(0).push(scn.nextInt());
        }

        for (int i = 1; i <= q; i++) {

            Stack ps = A.get(i - 1);

            while (!ps.isEmpty()) {

                int element = ps.pop();

                if (element % ithPrime(i) == 0) {
                    B.get(i).push(element);
                } else {
                    A.get(i).push(element);
                }

            }

        }

        for (int i = 1; i < B.size(); i++) {
            Stack ps = B.get(i);

            while (!ps.isEmpty()) {
                System.out.println(ps.pop());
            }

        }

        while (!A.get(q).isEmpty()) {
            System.out.println(A.get(q).pop());
        }

    }

    public static int ithPrime(int i) {

        int count = 0;
        int n = 2;

        while (true) {

            if (isPrime(n)) {
                count++;
            }

            if (count == i) {
                return n;
            }

            n++;
        }

    }

    public static boolean isPrime(int n) {

        int div = 2;

        while (div * div <= n) {
            if (n % div == 0) {
                return false;
            }

            div++;
        }

        return true;

    }
}