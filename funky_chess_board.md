Editorial: 💡 Funky Chess Board

This problem can be done using "recursion/dfs and similar" fashion. once you visit a cell, then visit all the cells that can be visited from this cell and also visit the cells that can be further visited from the next reachable cells.


#include<iostream>
#include<stdio.h>
#include<stdlib.h>
using namespace std;

int n,cols,empty,board[10][10],sum=0,hi;

void set(int i,int j,int count){
    if(i<0 || i>=10 || j<0 || j>=10 || board[i][j] == 0)
        return;
    int ans = 0;
    board[i][j] = 0;//unsets the (i,j) cell
    hi = max(hi,count+1);//hi stores the maximum of value of visited squares
    //try all 8 possible moves for knight
    set(i-1,j-2,count+1);
    set(i-2,j-1,count+1);
    set(i+1,j-2,count+1);
    set(i+2,j-1,count+1);
    set(i-1,j+2,count+1);
    set(i-2,j+1,count+1);
    set(i+1,j+2,count+1);
    set(i+2,j+1,count+1);
    board[i][j] = 1;//sets (i,j) cell again(backtracking)
}
int main(){
//    freopen("input.txt","r",stdin);

    cin>>n;
    sum = 0;

    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            cin>>board[i][j];
            if(board[i][j])
                sum++; // sum stroes total number of valid cells on chessboard
        }
    }
    hi=0;
    set(0,0,0);
    cout<<sum-hi<<"\n";
    return 0;
}
Lang - Java

public class Main {
    public static void main(String args[]) {

        Scanner scn = new Scanner(System.in);

        int n = scn.nextInt();

        int[][] arr = new int[n][n];
        int sum = 0;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {

                arr[i][j] = scn.nextInt();
                if(arr[i][j] == 1)
                    sum++; 
            }
        }

        funky(arr, sum);

    }



    static int n, cols, empty, sum = 0, hi;

    public static void set(int[][] board, int i, int j, int count) {
        if (i < 0 || i >= board.length || j < 0 || j >= board[0].length || board[i][j] == 0)
            return;
        int ans = 0;
        board[i][j] = 0;// unsets the (i,j) cell
        hi = Math.max(hi, count + 1);// hi stores the maximum of value of visited squares
        // try all 8 possible moves for knight
        set(board, i - 1, j - 2, count + 1);
        set(board, i - 2, j - 1, count + 1);
        set(board, i + 1, j - 2, count + 1);
        set(board, i + 2, j - 1, count + 1);
        set(board, i - 1, j + 2, count + 1);
        set(board, i - 2, j + 1, count + 1);
        set(board, i + 1, j + 2, count + 1);
        set(board, i + 2, j + 1, count + 1);
        board[i][j] = 1;// sets (i,j) cell again(backtracking)
    }

    public static void funky(int[][] board, int sum) {

        hi = 0;
        set(board, 0, 0, 0);
        System.out.print(sum - hi);
    }