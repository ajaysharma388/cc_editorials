Editorial: 💡 Strings-Remove Duplicates
X
1) Start from the leftmost character and remove duplicates at left corner if there are any.
2) The first character must be different from its adjacent now. Recur for string of length n-1 (string without first character).
3) Let the string obtained after reducing right substring of length n-1 be rem_str. There are three possible cases .

……..a) If first character of remstr matches with the first character of original string, remove the first character from remstr.
……..b) If remaining string becomes empty and last removed character is same as first character of original string. Return empty string.
……..c) Else, append the first character of the original string at the beginning of rem_str.

4) Return rem_str.


public static void remove(String str) {

        String ans = "";
        int i = 0;
        int j = i + 1;

        while (i < str.length() && j < str.length()) {

            if (str.charAt(i) != str.charAt(j)) {

                ans += str.charAt(i);
                i = j;
            }

            j++;

        }
        ans += str.charAt(str.length() - 1);

        System.out.println(ans);

    }