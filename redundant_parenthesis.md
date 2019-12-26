Editorial: 💡 Redundant Parentheses
X
The idea is to use stack. Iterate through the given expression and for each character in the expression, if the character is a open parenthesis ‘(‘ or any of the operators or operands, push it to the top of the stack. If the character is close parenthesis ‘)’, then pop characters from the stack till matching open parenthesis ‘(‘ is found and a counter is used, whose value is incremented for every character encountered till the opening parenthesis ‘(‘ is found. If the number of characters encountered between the opening and closing parenthesis pair, which is equal to the value of the counter, is less than or equal to 1, then a pair of duplicate parenthesis is found else there is no occurrence of redundant parenthesis pairs. For example, (((a+b))+c) has duplicate brackets around “a+b”. When the second “)” after a+b is encountered, the stack contains “((“. Since the top of stack is a opening bracket, it can be concluded that there are duplicate brackets.


// C++ program to find duplicate parenthesis in a
// balanced expression
#include <iostream>
#include <stack>
using namespace std;

// Function to find duplicate parenthesis in a
// balanced expression
bool findDuplicateparenthesis(string str)
{
    // create a stack of characters
    stack<char> Stack;

    // Iterate through the given expression
    for (char ch : str)
    {
        // if current character is close parenthesis ')'
        if (ch == ')')
        {
            // pop character from the stack
            char top = Stack.top();
            Stack.pop();

            // if immediate pop is a open parenthesis '(',
            // we have found duplicate
            if (top == '(')
                return true;

            // else we continue popping characters from the
            // stack till open parenthesis '(' is encountered
            else
            {
                while (top != '(')
                {
                    top = Stack.top();
                    Stack.pop();
                }
            }
        }

        // push open parenthesis '(', operators and
        // operands to stack
        else
            Stack.push(ch);
    }

    // No duplicates found
    return false;
}

// Driver code
int main()
{
    int t;
    cin>>t;
    for(int i=0;i<t;i++)
    {
        string str;
        cin>>str;
        if (findDuplicateparenthesis(str))
        cout << "Duplicate"<<endl;
       else
        cout << "Not Duplicates"<<endl;
    }
    // input balanced expression
    //string str = "(((a+(b))+(c+d)))";
    // string str = "((a+(b))+(c+d))";

    // if (findDuplicateparenthesis(str))
    //  cout << "Duplicate Found "<<endl;
    // else
    //  cout << "No Duplicates Found "<<endl;

    return 0;
}

Code

// Function to find duplicate parenthesis in a  
// balanced expression  
    static boolean findDuplicateparenthesis(String s) { 
        // create a stack of characters  
        Stack Stack = new Stack<>(); 

        // Iterate through the given expression  
        char[] str = s.toCharArray(); 
        for (char ch : str) { 
            // if current character is close parenthesis ')'  
            if (ch == ')') { 
                // pop character from the stack  
                char top = Stack.peek(); 
                Stack.pop(); 

                // stores the number of characters between a  
                // closing and opening parenthesis  
                // if this count is less than or equal to 1  
                // then the brackets are redundant else not  
                int elementsInside = 0; 
                while (top != '(') { 
                    elementsInside++; 
                    top = Stack.peek(); 
                    Stack.pop(); 
                } 
                if (elementsInside < 1) { 
                    return true; 
                } 
            } // push open parenthesis '(', operators and  
            // operands to stack  
            else { 
                Stack.push(ch); 
            } 
        } 

        // No duplicates found  
        return false; 
    } 