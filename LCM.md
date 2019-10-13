Editorial: 💡 LCM
X
Lang - Cpp
To find the LCM of two numbers, it is obvious that the LCM will be greater than or equal to the samller number in the two given numbers.

Algorithm

Take input of both the numbers say, N1 and N2.
Declare a variable with value with the smallest of the two numbers.
put a Infinite loop
Inside loop check if the variable can divide both the numbers,
If yes, break.
Otherwise increment the variable and continue.
Print the LCM obtained.
Code

#include<iostream>
int main() {
    int num1,num2;
    cin >> num1>>num2;

    if(num1>num2){
        int temp = num2;
        num2=num1;
        num1=temp;
    }

    int lcm=num2;
    while(lcm>0){
        if(lcm%num2==0 && lcm%num1==0){
            break;
        }
        lcm++;
    }
    cout << lcm << std::endl;
    return 0;
}
Lang - Java
The approach is to start with the largest of the 2 numbers and keep incrementing the larger number by itself till smaller number perfectly divides the resultant.


    public static int lcm(int n1, int n2){
        int largest = Math.max(n1, n2);
        int smallest = Math.min(n1, n2);

      for(int i = largest; ;i += largest){

          if(i % smallest == 0) return i;
      }
    }