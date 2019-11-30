Editorial: 💡 Increasing Decreasing Sequence

About the input, you need not to take array, one can also perform the question without using array. As every time we just check two consecutive numbers to tell whether the seqeunce is increasing or decreasing, so why should we store all of the numbers.

A sequence is true if you can split it into two sub sequence such that first sequence is strictly increasing and second sequence is strictly decreasing.
For e.g.,
1 2 3 4 5
This sequence is also true as we can split it into two sequence like., sequence one is empty and sequence two is 1 2 3 4 5.
Let's take another example.,
5 4 3 2 1
This is also true as we can split it such that sequence one is5 4 3 2 1 and sequence two is empty.
According to the problem statement, we can say the if the sequence decreases then it should not increase, if this is the case one can directly print false else print true.

Code

public static boolean valid_invalid(int n){

        int prev = scn.nextInt();
        int cnt = 1;
        boolean goingUp = false;
        boolean isValid = true;

        while(cnt < n){

            int curr = scn.nextInt();

            int diff = curr - prev;
             // As the sequence must be strctly decreasing or increasing
            if(diff == 0){  
                isValid = false;
            }else if(diff > 0){  // If Sequence is increasing 
                goingUp = true;
            }else if(goingUp && diff < 0){
              // If Sequence is Decreasing if its already increased once
                                isValid = false;
            }

            prev = curr;
            cnt++;

        }

        return isValid;
}