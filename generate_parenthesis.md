Editorial: 💡 Generate Parentheses
X
Algorithm:

Keep track of counts of open and close brackets.

Initialize these counts as 0.

Recursively call the generateParenthesis() function until open bracket count is less than the given n.

If open bracket count becomes more than the close bracket count, then put a closing bracket and recursively call for the remaining brackets.

If open bracket count is less than n, then put an opening bracket and call _printParenthesis() for the remaining brackets.

Lang - Cpp

#include <iostream>
using namespace std;

void generateParenthesis(int n, int openB, int closeB, string str) {
    if(closeB == n) {
        cout<<str<<endl;
        return;
    }
    if(openB > closeB) {
        generateParenthesis(n, openB, closeB+1, str+')');
    }
    if(openB < n) {
        generateParenthesis(n, openB+1, closeB, str+'(');
    }
}

int main(int argc, char const *argv[])
{
    /* code */
    generateParenthesis(3, 0, 0, "");
    return 0;
}

Lang - Java

public static void printParenthesis(int n, String ans, int close, int limit, int open) {

        if (n == 0) {
            System.out.println(ans);
            return;
        }

        if(close < open && open != 0) {
            printParenthesis(n - 1, ans + ")", close + 1, limit, open);
        }
        if (open < limit) {
            printParenthesis(n - 1, ans + "(", close, limit, open + 1);
        }
    }