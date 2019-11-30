Editorial: 💡 Arrays-Wave print Column Wise

For the case:

4 5

1 2 3 4 5

6 7 8 9 10

11 12 13 14 15

16 17 18 19 10

In wave print column wise, for each column we need to print elements of each row starting from 0th(min) row to 4th(max) row and from 4th (max) row to 0th(min) row alternatively.



Thus, output is 1, 6, 11, 16, 17, 12, 7, 2, 3, 8, 13, 18, 19, 14, 9, 4, 5, 10, 15, 10, END


Required Code is given below :


#include <iostream>
using namespace std;
int main() {
    int nRow,nCol;
    cin >> nRow >> nCol;

    int a[nRow][nCol];

//Take Input
    for (int i = 0; i < nRow; i++) {
        for (int j = 0; j < nCol; j++) {
            cin >> a[i][j];
        }
    }
    //Iterating over each column 
    for (int j = 0; j < nCol; j++) {

//for odd columns printing elements of rows from max row to min row 
//for even columns printing elements of rows from min row to max row
//Thus forming a wave pattern.
        if( j%2!=0){
            //for odd column
            for (int i = nRow-1; i >= 0; i--) {
                cout << a[i][j] << ", ";
            }
        }else{
            //for even column
            for (int i = 0; i < nRow; i++) {
                cout << a[i][j] << ", ";
            }
        }
    }
    cout << "END" <<endl;
}
Lang - Java

 public static void waveCol(int[][] arr) {

        for (int col = 0; col < arr[0].length; col++) {

            if (col % 2 == 0) {
                for (int row = 0; row < arr.length; row++) {
                    System.out.print(arr[row][col] + ", ");
                }
            } else {
                for (int row = arr.length - 1; row >= 0; row--) {
                    System.out.print(arr[row][col] + ", ");
                }
            }
        }

        System.out.println("END");
    }