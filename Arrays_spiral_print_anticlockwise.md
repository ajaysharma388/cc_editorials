Editorial: 💡 Arrays-Spiral Print Anticlockwise

For the given case:

4 4

1 2 3 4

5 6 7 8

9 10 11 12

13 14 15 16

In sprial print anti-clockwise, we need to print elements of first column then elements of last row then elements of last column then elements of first row and so on until all the elements of the matrix are printed. In the given case first the elements of 0th column then of 3rd row then of 3rd column then of 0th row then of 1st column then of 2nd row then of 2nd column are printed.Thus, elements are printed column and row wise alternatively forming an anti-clockwise loop.



Program for spiral printing of elements of 2-d array is given below:


#include <stdio.h>
#include <iostream>
using namespace std;
int main()
{
   int m, n;
    cin >> m >> n;
    int ut, uj;
    int a[m][n];
    for (ut = 0; ut < m; ut++)
        for (uj = 0; uj < n; uj++)
            cin >> a[ut][uj];

 int i, k = 0, l = 0;

    /*  k - starting row index
        m - ending row index
        l - starting column index
        n - ending column index
        i - iterator
    */

    while (k < m && l < n)
    {

        /* Print the first column from the remaining columns */
        for (i = k; i < m; ++i)
            {
                printf("%d, ", a[i][l]);
            }
            l++;    


        /* Print the last row from the remaining rows */
        for (i = l; i < n; ++i)
            {
                printf("%d, ", a[m-1][i]);
            }
            m--;


        /* Print the last column from the remaining columns */
        for (i = m-1; i >=k; --i)
        {
            printf("%d, ", a[i][n-1]);
        }
        n--;



        /* Print the first row from the remaining rows */
        for (i = n-1; i >=l; --i)
        {
            printf("%d, ", a[k][i]);
        }
        k++;
    }
    cout << "END";
    return 0;
}

Lang - Java

public static void spiralDisplay(int[][] arr) {
        int rmin = 0;
        int rmax = arr.length - 1;
        int nel = arr.length * arr[0].length;
        int cmin = 0;
        int cmax = arr[0].length - 1;
        int counter = 0;
        while (counter < nel) {

            for (int row = rmin; counter < nel && row <= rmax; row++) {
                System.out.print(arr[row][cmin] + ", ");
                counter++;
            }
            cmin++;
            for (int col = cmin; counter < nel && col <= cmax; col++) {
                System.out.print(arr[rmax][col] + ", ");
                counter++;
            }
            rmax--;
            for (int row = rmax; counter < nel && row >= rmin; row--) {
                System.out.print(arr[row][cmax] + ", ");
                counter++;
            }
            cmax--;

            for (int col = cmax; counter < nel && col >= cmin; col--) {
                System.out.print(arr[rmin][col] + ", ");
                counter++;
            }
            rmin++;
        }
        System.out.println("END");
    }