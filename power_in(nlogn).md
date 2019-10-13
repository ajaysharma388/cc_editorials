Editorial: 💡 Power(O(logn))
X
Using divide and conquer technique we can observe the following recurrence
power(x, n) = power(x, n / 2) * power(x, n / 2); // else n is even
power(x, n) = x * power(x, n / 2) * power(x, n / 2); // if n is odd


#include<iostream>
using namespace std;

float power(float x, int y)
{
    float temp;
    if( y == 0)
       return 1;
    temp = power(x, y/2);       
    if (y%2 == 0)
        return temp*temp;
    else
    {
        if(y > 0)
            return x*temp*temp;
        else
            return (temp*temp)/x;
    }
}  

int main() {
    int num,pw;
    cin>>num>>pw;
    cout<<power(num,pw);
    return 0;
}
Lang - Java

 public static int power(int x, int y) {
        int temp = 0;
        if (y == 0)
            return 1;
        temp = power(x, y / 2);
        if (y % 2 == 0)
            return temp * temp;
        else {
            if (y > 0)
                return x * temp * temp;
            else
                return (temp * temp) / x;
        }
    }