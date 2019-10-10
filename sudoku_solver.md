Editorial: 💡 SUDOKU SOLVER
X
We can solve Sudoku by one by one assigning numbers to empty cells. Before assigning a number, we check whether it is safe to assign. We basically check that the same number is not present in the current row, current column and current 3X3 subgrid. After checking for safety, we assign the number, and recursively check whether this assignment leads to a solution or not. If the assignment doesn’t lead to a solution, then we try next number for the current empty cell. And if none of the number (1 to 9) leads to a solution, we return false.

Find row, col of an unassigned cell
If there is none, return true
For digits from 1 to 9
a) If there is no conflict for digit at row, col assign digit to row, col and recursively try fill in rest of grid
b) If recursion successful, return true
c) Else, remove digit and try another
If all digits have been tried and nothing worked, return false

#include<iostream>
using namespace std;

int n;
bool canPlace(int mat[][9],int x,int y,int val){
    ///Check along row
    for(int i=0;i<n;i++){
        if(mat[x][i]==val){
            return false;
        }
    }
    ///Check along col
    for(int i=0;i<n;i++){
        if(mat[i][y]==val){
            return false;
        }
    }
    ///Check along subgrid
    int sx = (x/3)*3;
    int sy = (y/(n/3))*(n/3);

    for(int i=sx;i<sx+3;i++){
        for(int j=sy;j<sy+(n/3);j++){
            if(mat[i][j]==val){
                return false;
            }
        }
    }
    return true;
}

bool solveSudoku(int mat[][9],int i,int j){
    if(i==n){
        return true;
    }
    if(j==n){
        return solveSudoku(mat,i+1,0);
    }
    if(mat[i][j]!=0){
        return solveSudoku(mat,i,j+1);
    }
    else{
        ///Hume fill krna
        for(int no=1;no<=n;no++){
            if(canPlace(mat,i,j,no)){
                mat[i][j] = no;
                bool solveHua = solveSudoku(mat,i,j+1);
                if(solveHua==true){
                    return true;
                }
            }

        }
        ///Backtracking
        mat[i][j]=0;
        return false;

    }
}




int main(){

        #ifndef ONLINE_JUDGE
        freopen("input.txt","r",stdin);
        freopen("out.txt","w",stdout);
        #endif
        int mat[9][9] =
        {{5,3,0,0,7,0,0,0,0},
        {6,0,0,1,9,5,0,0,0},
        {0,9,8,0,0,0,0,6,0},
        {8,0,0,0,6,0,0,0,3},
        {4,0,0,8,0,3,0,0,1},
        {7,0,0,0,2,0,0,0,6},
        {0,6,0,0,0,0,2,8,0},
        {0,0,0,4,1,9,0,0,5},
        {0,0,0,0,8,0,0,7,9}};
        /*
           for(int i=0;i<9;i++){
            for(int j=0;j<9;j++){
                cout<<mat[i][j]<<" ";
            }
            cout<<endl;
        }*/
        cin>>n;
        for(int i=0;i<n;i++)
        {
            for(int j=0;j<n;j++)
                cin>>mat[i][j];
        }
        solveSudoku(mat,0,0);

        //cout<<"Solved Sudoku "<<endl;
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                cout<<mat[i][j]<<" ";
            }
            cout<<endl;
        }
        return 0;
}
Lang - Java

public class Sudoku {

    public static void main(String[] args) {

        Scanner scn = new Scanner(System.in);

        int n = scn.nextInt();
        int[][] board = new int[n][n];

        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[0].length; j++) {
                board[i][j] = scn.nextInt();
            }
            // System.out.println();
        }

        Sudoku(board, 0, 0);

        display(board);
    }

    public static boolean Sudoku(int[][] board, int row, int col) {

        if (col == board[0].length) {
            row = row + 1;
            col = 0;
        }

        if (row == board.length) {
            // display(board);
            return true;
        }

        if (board[row][col] != 0) {
            return Sudoku(board, row, col + 1);

        }

        for (int i = 1; i <= 9; i++) {

            if (isItSafe(board, row, col, i)) {

                board[row][col] = i;

                boolean res = Sudoku(board, row, col + 1);

                if (res)
                    return true;

                board[row][col] = 0;

            }
        }

        return false;

    }

    public static boolean isItSafe(int[][] board, int row, int col, int val) {

        return isItSafeRow(board, row, val) && isItSafeCol(board, col, val) && isItSafeCell(board, row, col, val);
    }

    public static boolean isItSafeRow(int[][] board, int row, int val) {

        for (int col = 0; col < board[0].length; col++) {
            if (board[row][col] == val) {
                return false;
            }
        }

        return true;
    }

    public static boolean isItSafeCol(int[][] board, int col, int val) {

        for (int row = 0; row < board.length; row++) {
            if (board[row][col] == val) {
                return false;
            }
        }

        return true;
    }

    public static boolean isItSafeCell(int[][] board, int row, int col, int val) {

        int rs = row - row % 3;
        int cs = col - col % 3;

        for (int r = rs; r < rs + 3; r++) {
            for (int c = cs; c < cs + 3; c++) {

                if (board[r][c] == val) {
                    return false;
                }
            }
        }

        return true;
    }

    public static void display(int[][] board) {

        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[0].length; j++) {
                System.out.print(board[i][j] + " ");
            }
            System.out.println();
        }
    }
}