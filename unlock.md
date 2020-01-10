Editorial: 💡 Unlock

The following problem canbe easily solved by using hashmap or unordered map. The hint to solve the problem is that the given array will always contain permutation of the first N natural numbers. So we will prepare a map which will contain element as the key and the index at which it is present as the value.

Algorithm

Create the map by filling the number as the key and the index at which it is present as the value
Iterate over the whole array.
For element at a particular index m we will check if it is present at its best spot or not.
The best spot of any number num is the N-num index of the array.
If the number is not present at its best spot then we will swap the number with element present at that spot.
As we have stored the index of every element in the map we can easily retrieve that from the map to get the swap done.

import java.util.HashMap;
import java.util.Scanner;

public class unlock {

    public static void main(String[] args) {

        Scanner scn = new Scanner(System.in);
        int n = scn.nextInt();
        int k=scn.nextInt();
        int[] arr = new int[n];
        HashMap<Integer, Integer> map = new HashMap();
        for (int i = 0; i < n; i++) {
            arr[i] = scn.nextInt();
            map.put(arr[i], i);
        }
        int num=n;
        int m=0;
        while(m<n && k>0) {
            int hold = map.get(num-m);
            if(hold==n-num+m) { // Check if the number is present at the best spot
                m++;
                continue;
            } else { // If the number is not present at the best spot then swap the number with the element at that spot 
                int temp=arr[m];
                arr[m]=arr[hold];
                arr[hold]=temp;
                map.put(arr[hold], hold);
                map.put(arr[m],m);
                m++;
                k--;
            }
        }
        for(int i=0;i<arr.length;i++) {
            System.out.print(arr[i]+" ");
        }
    }
}