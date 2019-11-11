Editorial: 💡 Prateek Sir and Coding

Algo:

Check the Type of the query entered.
If it is 1 then,
…..2.1 pop and print the book.
…..2.2 If stack is empty print No Code otherwise print price.
Repeat the work till the q is vanished.
Code

 public static void prateekSirCoding() {

        Scanner scn = new Scanner(System.in);

        int q = scn.nextInt();
        Stack stack = new Stack<>();
        while (q-- > 0) {

            int type = scn.nextInt();

            if (type == 1) {

                if (!stack.isEmpty()) {
                    System.out.println(stack.pop());
                }else {
                    System.out.println("No Code");
                }

            } else {

                stack.push(scn.nextInt());
            }
        }

    }