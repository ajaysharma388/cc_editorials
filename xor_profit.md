Editorial: 💡 XOR Profit Problem
X
A simple solution is to generate all pairs, find their XOR values and finally return the maximum XOR value.
An efficient solution is to consider pattern of binary values from L to R. We can see that first bit from L to R either changes from 0 to 1 or it stays 1 i.e. if we take the XOR of any two numbers for maximum value their first bit will be fixed which will be same as first bit of XOR of L and R itself. After observing the technique to get first bit, we can see that if we XOR L and R, the most significant bit of this XOR will tell us the maximum value we can achieve i.e. let XOR of L and R is 1xxx where x can be 0 or 1 then maximum XOR value we can get is 1111 because from L to R we have all possible combination of xxx and it is always possible to choose these bits in such a way from two numbers such that their XOR becomes all 1.


#include "iostream"
using namespace std;
int main(int argc, char* argv[])
{
    int x,y;
    cin>>x>>y;
    int num = x^y;
    int msb=0;
    while(num!=0) {
        num=num>>1;
        msb++;
    }
    int result = 1;
    while(msb--) {
        result=result<<1;
    }
    cout<<result-1;

    return 0;
}

Lang - Java

public static int profit(int x, int y) {

        int num = x ^ y;
        int msb = 0;
        while (num != 0) {
            num = num >> 1;
            msb++;
        }
        int result = 1;
        while (msb-- > 0) {
            result = result << 1;
        }
        return result - 1;
    }