Editorial: 💡 Maximum length Biotonic Subarray

Algorithm

Initialize I[0] to 1 and D[n-1] to 1

Creating I[] array
a. Till end of the array ie, i=1 to n, if arr[i] > arr[i-1] then I[i] = I[i-1] + 1. else, I[i] = 1

Creating D[] array
a. From the end of the array ie, i = n-2 till i =0, if arr[i] > arr[i+1] then D[i] = D[i +1] +1 else, D[i] = 1

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner scn = new Scanner(System.in);
        int t=scn.nextInt();
        while(t-- > 0) {
        int n = scn.nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < arr.length; i++) {
            arr[i] = scn.nextInt();
        }
        System.out.println(bitonic(arr));
        }
    }

    public static int bitonic(int arr[]) 
    { 
        int n=arr.length;
        int[] inc = new int[n]; 

        int[] dec = new int[n]; 
        int max; 

        inc[0] = 1; 
        dec[n-1] = 1; 
        for (int i = 1; i < n; i++) 
           inc[i] = (arr[i] >= arr[i-1])? inc[i-1] + 1: 1; 
        for (int i = n-2; i >= 0; i--) 
            dec[i] = (arr[i] >= arr[i+1])? dec[i+1] + 1: 1; 
        max = inc[0] + dec[0] - 1; 
        for (int i = 1; i < n; i++) 
            if (inc[i] + dec[i] - 1 > max) 
                max = inc[i] + dec[i] - 1; 

        return max; 
    } 
}