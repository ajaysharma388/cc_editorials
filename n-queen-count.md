Editorial: 💡 COUNT N-QUEEN
X
1) Start in the leftmost column .
2) If all queens are placed return true .
3) Try all rows in the current column. Do following for every tried row.

If the queen can be placed safely in this row then mark this [row, column] as part of the solution and recursively check if placing queen here leads to a solution.
If placing the queen in [row, column] leads to a solution then return true.
If placing queen doesn't lead to a solution then umark this row, column and go to step (a) to try other rows.
If all rows have been tried and nothing worked, return false to trigger backtracking.

import java.util.*;

public class Main {

    public static void main(String[] args) {
    Scanner scn = new Scanner(System.in);
    int n=scn.nextInt();
        System.out.println(countNquens(n));

    }
    public static int countNquens(int n) {
        boolean[][] board = new boolean[n][n];
        return countNqueens(board, 0);
    }

    public static int countNqueens(boolean[][] board, int row) {
        if (row == board.length) {
            return 1;
        }
        int count = 0;
        for (int col = 0; col < board[row].length; col++) {
            if (isitsafetpq(board, row, col)) {
                board[row][col] = true;
                count += countNqueens(board, row + 1);
                board[row][col] = false;
            }
        }
        return count;
    }

    public static boolean isitsafetpq(boolean[][] board, int row, int col) {// check
                                                                            // col
        for (int i = row - 1; i >= 0; i--) {
            if (board[i][col]) {
                return false;
            }
        }
        // check diagnol
        for (int i = row - 1, j = col - 1; i >= 0 && j >= 0; i--, j--) {
            if (board[i][j]) {
                return false;
            }
        }

        for (int i = row - 1, j = col + 1; i >= 0 && j < board.length; i--, j++) {
            if (board[i][j]) {
                return false;
            }
        }

        return true;
    }

}