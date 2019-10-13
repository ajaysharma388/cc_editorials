Editorial: 💡 GCD
X
Euclidean algorithm

The algorithm is based on below facts.

If we subtract smaller number from larger (we reduce larger number), GCD doesn’t change.
So if we keep subtracting repeatedly the larger of two, we end up with GCD.
Now instead of subtraction, if we divide smaller number, the algorithm stops when we find remainder 0.
Lang - Cpp

#include<iostream>
using namespace std;

int gcd(int a,int b){
    return b==0?a:gcd(b,a%b);
}

int main() {
    int n1,n2;
    cin>>n1>>n2;
    cout<<gcd(n1,n2)<<endl;
    return 0;
}
Lang - Java
Long Division Method
Finding highest common factor (H.C.F) by prime factorization for large number is not very convenient. The method of long division is more useful for large numbers.

We use the repeated division method for finding highest common factor (H.C.F) of two or more numbers. To find highest common factor by using division method we follow these steps: Step I: Divide the large number by the smaller one.
Step II: Then the remainder is treated as divisor and the divisor as dividend.
Step III: Divide the first divisor by the first remainder.
Step IV: Divide the second divisor by the second remainder.
Step V: Continue this process till the remainder becomes 0.
Step VI:The divisor which does not leave a remainder is the H.C.F. or G.C.D. of the two numbers and thus, the last divisor is the required highest common factor (H.C.F) of the given numbers.

Let us consider some of the examples to find highest common factor (H.C.F) by using division method.

Figure

Code

 public static int gcd(int dividend, int divisor){

    while(dividend % divisor != 0){
        int rem = dividend % divisor;
        dividend = divisor;
        divisor = rem;
    }

    return divisor;
    }