Editorial: 💡 Recursion-Duplicate character formatting
X
In this question, the idea is to put a recursive function on the Array and print * if we got any repetitive character.

Algorithm:

If length of the string is 1, return the string.
Self work is to check if the first two characters of the string are equal. If they are, insert a * between the two characters. Then, perform a recursive call for the rest of the string excluding the two characters.
Else perform the recursive call for the next character.