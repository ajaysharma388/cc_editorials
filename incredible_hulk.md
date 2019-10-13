Editorial: 💡 Incredible Hulk
X
Let total steps is n, find the nearest integer which is of power 2 and less then n. let it would be k. now remaining steps to cover is n-k and result = 1 + min steps for (n-k) remaining steps.


#include <iostream>
using namespace std;
long long convertDecimalToBinary(unsigned long long int);
int main ()
{
    unsigned long long int n;
 // Number of test case
    cin >> n;
    unsigned long long int arr[n], i;
// Input for each test case
    for (i = 1; i <= n; i++)
        cin >> arr[i-1];

    for (i = 0; i < n; i++)
    {
        unsigned long long int binaryNumber, sum = 0;
     //Function to convert binary to decimal
        binaryNumber = convertDecimalToBinary(arr[i]);

        while (binaryNumber != 0)
        {
            unsigned long long int t;
            t = binaryNumber%2;
            sum = sum + t;
            binaryNumber = binaryNumber/10;
        }
        cout << sum << endl;
    }
    return 0;
}
//Function to convert Binary to decimal
long long convertDecimalToBinary(unsigned long long int n)
{
    long long binaryNumber = 0;
    unsigned long long int remainder, i = 1, step = 1;

    while (n!=0)
    {
        remainder = n%2;
        n /= 2;
        binaryNumber += remainder*i;
        i *= 10;
    }
    return binaryNumber;
}
Lang - Java
In short the Question is to find he highest power of 2 which is smaller than or equals to the given number. Solution contains Bit Masking code and also attaching the algo for the code and hence you can also implement the same code without using bit masking if anyone is not comfortable with the bit masking approach. But do read the algo once.

Algo

Check if the number is power of 2 .
For e.g., n = 4 so 4 & 3 == 1 ? hence power of 2.
…..1.1 If yes then return 1.
Count the number of set bits.
This count is the answer.

public static int minSteps(int n) {

        if ((n & (n - 1)) == 1)
            return 1;

        int sum = 0;
        int mask = n;
        while (mask != 0) {

            sum += mask & 1;
            mask >>= 1;

        }

        return sum;
    }