Editorial: 💡 Rotate Image (N X N Array)

A simple trick that we can observe is that we can first transpose the whole matrix along the leading diagonal and then reverse each row of the matrix. The resulting matrix will be out the rotated matrix. Here is the code for the following algorithm.


#include <iostream>
using namespace std;
int main(int argc, char* argv[])
{
    int n,m;
    std::cin >> n;
    m=n;
    int array[n][m];
    for(int i=0;i<n;i++) {
        for(int j=0;j<m;j++) {
            cin>>array[i][j];
        }
    }

    for(int i=0;i<n;i++) {
        for(int j=i;j<m;j++) {
            swap(array[i][j],array[j][i]);
        }
    }

    for(int i=0;i<n;i++) {
        int lo = 0;
        int hi = n-1;
        while(lo<=hi) {
            swap(array[lo][i], array[hi][i]);
            lo++;
            hi--;
        }
    }

    for(int i=0;i<n;i++) {
        for(int j=0;j<m;j++) {
            cout<<array[i][j]<<" ";
        }
        cout<<endl;
    }

    return 0;
}

Lang - Java

 public static void rotate(int[][] matrix) {

        transpose(matrix);
        for (int j = 0; j < matrix[0].length; j++) {
            for (int i = 0; i < matrix.length / 2; i++) {

                int temp = matrix[i][j];
                matrix[i][j] = matrix[matrix.length - i - 1][j];
                matrix[matrix.length - i - 1][j] = temp;
            }
        }
             display(matrix);
    }

    public static void transpose(int[][] matrix) {

        for (int i = 0; i < matrix.length; i++) {
            for (int j = i; j < matrix[0].length; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
    }
    public static void display(int[][] matrix) {

        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[0].length; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();
        }
    }