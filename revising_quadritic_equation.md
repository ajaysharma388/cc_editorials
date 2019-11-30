Editorial: 💡 Revising Quadratic Equations
X
The input corresponds to equation ax^2 + bx + c = 0. Roots = (-b + sqrt(b^2 - 4ac))/2a , (-b - sqrt(b^2 - 4ac))/2a

Algo:

Calculate the D viz, sqrt(b * b - 4 * a * c).
If D < 0,
2.1 print Imaginary
if D == 0,
3.1 print Real and Equal
3.1 Calculate roots using formula ( - b + D) / (2 * a) and (- b - D)/ (2 * a)
3.2 Print the roots
If D > 0,
4.1 print Real and Distinct
4.2 Calculate roots using formula ( - b + D) / (2 * a) and (- b - D)/ (2 * a)
4.3 print the roots
End
Lang - Cpp

#include <iostream>
#include <math.h>
#include <cmath>
using namespace std;
int main ()
{
    float a, b, c;
    cin >> a >> b >> c;
    float d;
    float d1;
    d = b*b - 4*a*c;
    d1 = sqrt(d);
    if (d == 0)
        cout << "Real and Equal";
    else if (d >= 0)
        cout << "Real and Distinct";
    else if (d < 0)
        cout << "Imaginary";
    cout << endl;
    int x1, x2;
    if (d >= 0)
    {  
    x1 = (-b - d1)/(2*a);
    x2 = (-b + d1)/(2*a);
    cout << x1 << " " << x2;
    }
    return 0;
}
Lang - Java

 public static void printRoots(int a, int b, int c){


        int d = (b * b) - (4 * a * c);

        int root1 = 0;
        int root2 = 0;

        if(d < 0){
            System.out.println("Imaginary");
            return;
        }

        if(d == 0){

            System.out.println("Real and Equal");
        }else if(d >0){
            System.out.println("Real and Distinct");
        }

            root1 = (int) ((- b - Math.sqrt(d)) / (2 * a));
            root2 = (int) ((- b + Math.sqrt(d)) / (2 * a));

        System.out.println(root1 +" "+root2);

    }