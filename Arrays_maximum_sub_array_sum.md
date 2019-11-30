Editorial: 💡 Maximum Subarray Sum
X


A simple solution is to iterate through all the elements of the array. For every element, calculate the max contiguous subarray sum starting from that element itself.

Time complexity: O(n2).
An efficient way is to use Kadane’s Algorithm. Kadane’s algorithm is a Dynamic Programming approach to find the largest sum of contiguous subarray with runtime of O(n).Simple idea of the Kadane’s algorithm is to look for all positive contiguous segments of the array . And keep track of maximum sum contiguous segment among all positive segments .

Algo:

1.Take two variables one for storing local max sum(max-ending-here) and global max sum(max-so-far).
2.Iterate over each each element of the array say a.

  2.1 max_ending_here = max_ending_here + a[i]
  2.2 if(max_ending_here < 0)   
        max_ending_here = 0
  2.3 if(max_so_far < max_ending_here)
        max_so_far = max_ending_here
3.max-so-far is the required max sum of contiguous subarray.

Code:

// C++ program to print largest contiguous array sum
#include<iostream>
#include<climits>
using namespace std;

int maxSubArraySum(int a[], int size)
{
    int max_so_far = INT_MIN, max_ending_here = 0;

    for (int i = 0; i < size; i++)
    {
        max_ending_here = max_ending_here + a[i];
        if (max_so_far < max_ending_here)
            max_so_far = max_ending_here;

        if (max_ending_here < 0)
            max_ending_here = 0;
    }
    return max_so_far;
}
int main()
{
    int t;
    cin>>t;
    for(int j=0;j<t;j++)
    {
    int n;
    cin>>n;
    int a[n];
    for(int i=0;i<n;i++)
    {
        cin>>a[i];
    }
    int max_sum = maxSubArraySum(a, n);
    cout << max_sum<<endl;
    }
    return 0;
}

Lang - Java

class Kadane { 

    static int maxSubArraySum(int a[], int size) 
    { 
        int max_so_far = Integer.MIN_VALUE, 
        max_ending_here = 0,start = 0, 
        end = 0, s = 0; 

        for (int i = 0; i < size; i++)  
        { 
            max_ending_here += a[i]; 

            if (max_so_far < max_ending_here)  
            { 
                max_so_far = max_ending_here; 
                start = s; 
                end = i; 
            } 

            if (max_ending_here < 0)  
            { 
                max_ending_here = 0; 
                s = i + 1; 
            } 
        } 
        return s;
    } 