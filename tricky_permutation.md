Hacks
To Solve any Problem related to Recursion All you need to do is Break the Problem into 3 important components which are as follows :-

1.Bigger Problem : The original Problem statement is your bigger problem.
2.Smaller Problem: In every recursive prblm there exist a prblm statement which you need to achieve in order to fullfill the prblm statement but by considering such a smaller prblm from the bigger prblm is needed which we need to assume that the recursion will work and will give the answer.
3.Self Work: The amount of work which one should do in order to make the smaller problem your problem.

For e.g.., In order to find the max of any array, three components will be :-
Bigger Problem : To find the max in whole array viz find max in array from index 0 to n - 1.
Smaller Problem: Assume that the recursion works and will find the max of array from index 1 to n - 1.
Self Work : In order to make your smaller prblm your bigger prblm all you need to do is to compare the ans return by assuming the smaller prblm works with the 0th index element and return the max among both of them.

Similarly Classification acc to the Given prblm :-

Bigger Problem : To Print all of the possible permutations.
Smaller Problem : Assume the recursion works and will give you ans for permutations of String except first character.
Self Work: In order to make you smaller prblm your problem all you need to work for the 0th index element. Because it could be the part included in the answer or not. So, the 0th element will be added to every possible position.
For e.g.. ABC suppose the ans for BC can be available by recursion viz, BC and CB your work is the place A at every possible position in BC and CB. like, BC and BC and BC_ where the _ shows the possible position where A must be added.

Code

public class Main {
    public static void main(String args[]) {

        Scanner scn = new Scanner(System.in);

        String str = scn.next();

        char[] charray = str.toCharArray();
        Arrays.sort(charray);

       permutationNoDuplicates(new String(charray), "");
    }

   public static void permutationNoDuplicates(String ques, String ans) {

        if (ques.length() == 0) {
            System.out.println(ans);
            return;
        }

        for (int i = 0; i < ques.length(); i++) {

            char ch = ques.charAt(i);
            String roq = ques.substring(0, i) + ques.substring(i + 1);

            boolean flag = true;

            for (int j = i + 1; j < ques.length(); j++) {
                if (ques.charAt(j) == ch) {
                    flag = false;
                }
            }

            if (flag)
                permutationNoDuplicates(roq, ans + ch);
        }

    }
}

