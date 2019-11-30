Editorial: 💡 Maximum Circular Sum
X
This Question can be done using the brute force viz, by using two nested loops and checking the sum of every possible subset but this approach is in O(n^2). So, Now we are going to discuss an approach which solves the given problem in O(n).

Approach :
For finding the Maximum Contiguous sum we are using the kadane's algorithm. But in the question the array is circular that means the maximum sum can be of elements which are a part of the wrapping or not. So,
There can be two cases for the maximum sum:
Case 1: The elements that contribute to the maximum sum are arranged such that no wrapping is there. Examples: {-10, 2, -1, 5}, {-2, 4, -1, 4, -1}. In this case, Kadane’s algorithm will produce the result.

Case 2: The elements which contribute to the maximum sum are arranged such that wrapping is there. Examples: {10, -12, 11}, {12, -5, 4, -8, 11}. In this case, we change wrapping to non-wrapping. Let us see how. Wrapping of contributing elements implies non wrapping of non contributing elements, so find out the sum of non contributing elements and subtract this sum from the total sum. To find out the sum of non contributing, invert sign of each element and then run Kadane’s algorithm. Our array is like a ring and we have to eliminate the maximum continuous negative that implies maximum continuous positive in the inverted arrays.

Java Solution

public class maxCircularSum{
    public static void main(String[] args){

    Scanner scn = new Scanner(System.in);

    int t = new nextInt();

    while(t > 0){

        int n = scn.nextInt();

        int[] arr = new int[n];

        for(int i =0;i < n;i++)
            arr[i] = scn.nextInt();

        System.out.println(maxSum(arr));

        t--;
    }
  }

  public static int maxSum(int[] arr){

    int max_kadane = kadanes(arr);

    int max_wrap = 0;

    for(int i =0;i < arr.length;i++){
        max_wrap += arr[i];
        arr[i] = -arr[i];
    }

    int non_contib_sum = kadanes(arr);
    max_wrap = max_wrap + non_contib_sum;

    return (max_wrap > max_kadane?max_wrap:max_kadane);

  }

    public static int kadanes(int[] A) {

        int max_so_far = 0;
        int max_ending_here = 0;


        for(int i = 0;i < A.length;i++){

            max_ending_here += A[i];

            if(max_ending_here < 0){
                max_ending_here = 0;
            }

            if(max_so_far < max_ending_here){
                max_so_far = max_ending_here;
            }
        }
        return max_so_far;
    }
}
C++ Solution


#include
using namespace std;
// Standard Kadane's algorithm to find maximum subarray sum
int kadane(int a[], int n);

// The function returns maximum circular contiguous sum in a[]
int maxCircularSum(int a[], int n)
{
// Case 1: get the maximum sum using standard kadane's algorithm
int max_kadane = kadane(a, n);

// Case 2: Now find the maximum sum that includes
// corner elements.
int max_wrap = 0, i;
for (i=0; i max_kadane)? max_wrap: max_kadane;
}

// Standard Kadane's algorithm to find maximum subarray sum
int kadane(int a[], int n)
{
    int max_so_far = 0, max_ending_here = 0;
    int i;
    for (i = 0; i < n; i++)
    {
        max_ending_here = max_ending_here + a[i];
        if (max_ending_here < 0)
            max_ending_here = 0;
        if (max_so_far < max_ending_here)
            max_so_far = max_ending_here;
    }
    return max_so_far;
}

/* Driver program to test maxCircularSum() */
int main()
{
    int t;
    cin>>t;
    for(int i=0;i>n;
       int a[n];
       for(int j=0;j>a[j];
       }
        cout<< maxCircularSum(a, n) <