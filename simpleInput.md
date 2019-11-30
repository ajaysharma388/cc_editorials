Editorial: 💡 Simple Input

Many of you are Wondering where is the N(No of inputs specified)?

Till when we need to take input??

Ans to the question is present in the question itself, as it said print the numbers till u get positive cumulative sum, so u need to take input till u got the positive cumulative irrespective of the number inputs.

Algo:

Put a loop till the END OF INPUT.
Add the new number to the previous sum.
If the sum is positive print the current number.
Otherwise, break the loop.

 public static void takeInput(){

        Scanner scn = new Scanner(System.in);
        int sum = 0;

        while(sum >= 0){

            int n = scn.nextInt();
            sum += n;

            if(sum < 0) break;
            System.out.println(n);
        }
    }