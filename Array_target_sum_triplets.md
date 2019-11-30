Editorial: 💡 Arrays-Target Sum Triplets

For the sample case, Array = {5, 7, 9, 1, 2, 4, 6 ,8 ,3}. Target number = 10.Find any three numbers in the given array whose sum is equal to the target number. In this case triplets are:

1, 2 and 7

1, 3 and 6

1, 4 and 5

2, 3 and 5

Algorithm:

1.Sort the element in ascending order

2.Make Three nested for loop for checking or finding three integer from the sorted array of size n whose sum is equal to given target number.

for i in range of 0 to n
    for j in range of i+1 to n
        for k in range of j+1 to n

                if (arr[i]+arr[j]+arr[k] == target)  then 
                      print these three numbers
3.Thus, all the triplets have been printed.