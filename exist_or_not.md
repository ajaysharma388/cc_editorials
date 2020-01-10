Editorial: 💡 Exist OR Not

This one is a pretty simple problem all we need to do is create a hashmap of all the elements present in the array. Then for each query check if the hashmap contains the element then we will print Yes otherwise print No. The checking of element from the hashmap will be done in O(1) so for answering Q queries time complexity required will be O(Q)

Code

public static void existOrNot() {

        Scanner scn = new Scanner(System.in);

        int t = scn.nextInt();

        while (t-- > 0) {

            HashMap map = new HashMap<>();

            int n = scn.nextInt();

            for (int i = 0; i < n; i++) {
                int val = scn.nextInt();
                map.put(val, map.getOrDefault(val, 0) + 1);
            }

            int q = scn.nextInt();
            while (q-- > 0) {

                if (map.containsKey(scn.nextInt())) {
                    System.out.println("Yes");
                } else {
                    System.out.println("No");
                }
            }
        }
    }