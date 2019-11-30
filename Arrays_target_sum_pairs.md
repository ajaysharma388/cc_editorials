Editorial: 💡 Arrays-Target Sum Pairs

For the sample case, array = [1,3,4,2,5] and target=5, we need to find two numbers whose sum is equal to the target.Here in this case target sum pairs are 1, 4 and 2 , 3.

Algorithm:

1.First sort the given array.
2.Now take two variables one as left and other as right starting from 0th and end index of the sorted array respectively.
3.Now iterate till left<right.
3.1 Calculate the sum of the elements at left and right position
3.1.1 If the sum is equal to the target then print both the elements. //printing target sum pairs
3.1.2 If the sum is less than the target then increase the left by 1
3.1.3 Else decrease the right by 1
4.End loop.Thus, all the pairs has been printed .


 public static void targetSum(int[] arr, int target){
        Arrays.sort(arr);
        int left = 0;
        int right = arr.length - 1;
        while (left < right) {
            int sum = arr[left] + arr[right];
            if (sum > target) {
                right--;
            } else if (sum < target) {
                left++;
            } else {
                System.out.println(arr[left] + " and " + arr[right]);
                left++;
                right--;
            }
        }
    }