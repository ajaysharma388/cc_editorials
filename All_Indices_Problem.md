Editorial: 💡 All Indices Problem
X
In this question, aim is to find all the indices at which a particular element M is found in the array of size n. A simple solution is to use ArrayList and keep storing the indices at which M is found in the array.
But the problem can be made interesting with a constraint that the size of the resultant array must be equal to the no. of occurrences of M in the array. Now, we cannot predefine the array because we don't know how many times a particular element will appear in the array without traversing it.

Algorithm:

Maintain a variable 'count' which keeps track of the no. of occurrences of M in the array. Pass it along the function call so that its value doesn't get intialised to zero with every new recursive call.
Check if each element is equal to M or not. If true, increment count and and perform a recursive call with n-1 elements.
Else, again perform a recursive call with n - 1 elements but without changing the value of count.
Base case is when the size of the array is 0, contract an array of size count and return the array.
Code

 public static int[] Allindice(int[] arr, int vidx, int item, int cnt) {

        if (vidx == arr.length) {
            int[] brr = new int[cnt];
            return brr;
        }

        if (arr[vidx] == item) {

            int[] rr = Allindice(arr, vidx + 1, item, cnt + 1);
            rr[cnt] = vidx;
            return rr;
        } else {
            return Allindice(arr, vidx + 1, item, cnt);

        }
    }