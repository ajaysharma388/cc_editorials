Editorial: 💡 Balanced Parenthesis

Question is pretty simple just keep the track of corresponding open and closed brackets.

Algo

1 . Each time you encounter an open bracket simply push it 		into stack.

2 . If you got any closed bracket.
	2.1 If the stack is empty return false.
	2.2 Check if the closed bracket matches the peek element of stack.

    2.3.1 If yes pop the element and continue.   
    2.3.2  else return false.
3 . At the end return true if stack is empty.

:) I Hope you dont need code for this self explanatory Algo