Editorial: 💡 Arrays-Intersection Of Two Arrays

We could index somehow one of the arrays, then iterate through the other array. Each element that is found in the index is pushed to the output and simultaneously removed from the index. Critical characteristics of this solution are then space taken by the index and time it takes to insert, find and remove items from it. Most of the data structures that could be used here take space proportional to number of items stored. In terms of time, hash table is probably the best option. It requires O(1) time to insert, find and remove items. If array lengths are n and m, it takes O(n) total time to index one array. Pass through the second array, including finding elements in the hash table would take O(m) time. Finally, removing elements that are found in the hash table would take O(min(m, n)) time in worst case. From structure size point of view, it makes sense to index the shorter of the arrays. Bottom line is that this solution requires O(n+m) time and O(min(n, m)) space.


#include <bits/stdc++.h>
using namespace std;
int main() {
    int i, k = 0, n, j;
    cin >> n;

    int arr[n], brr[n], crr[n];

    //Input for 1st array
    for (i = 0; i < n; i++)
        cin >> arr[i];

    //Input for 2nd array
    for (i = 0; i < n; i++)
        cin >> brr[i];

    //Comparing element of 1st array with 2nd array
    for (i = 0; i < n; i++) //Iterate through 1st array
    {
        for (j = 0; j < n; j++) //Iterate through 2nd array
        {

             // If element present in both of arrays store it in other array 
             // which contains intersection of both arrays.
            if (arr[i] == brr[j])
            {
                crr[k] = arr[i];
                k++;
                brr[j] = NULL;
                break;
            }
        }
    }
    sort (crr, crr+k);
    cout << "[";
   for (i = 0; i < k; i++)
       {
        cout << crr[i];
         if (i < k-1)
             cout << ", ";
         else if (i == k-1)
            cout << "]";
       }

    return 0;
}

Lang - Java
Algorithm

Sort both of the Arrays.
Using TwoPointers approach check each element simultaneously.
…..If the element of first array is smaller then increment its pointer.
…..else if the element of the second array is smaller then increment its pointer.
…..else add the ans to an arrayList.


    public static void Intersection(int[] one, int[] two) {

        Arrays.sort(one);
        Arrays.sort(two);

        int i = 0;
        int j = 0;
        ArrayList<Integer> ans = new ArrayList<>();
        while (i < one.length && j < two.length) {

            if (one[i] < two[j]) {
                i++;
            } else if (one[i] > two[j]) {
                j++;
            } else {
                ans.add(one[i]);
                i++;
                j++;
            }
        }

        System.out.println(ans);


    }