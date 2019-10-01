In this case, the base case you're probably looking for is an empty array. The way to tie the problem to a smaller problem is to break your input list into two pieces: the last element of the input, and the list of elements before the last element. The list of elements before the last element is your smaller problem; the last element is how you decide whether you need to solve the smaller problem or not. Consider this set of questions:

Is the last element of my input the element I'm looking for? If so, how many elements are before it?
Otherwise, what's the answer to the above set of questions if I remove the current last element and try again?
In this case, recursion is the 'try again'.

public static int lastindex(int[] arr, int num, int si) {
        if (si == arr.length)
            return -1;

        int li = lastindex(arr, num, si + 1);
        if (li != -1)
            return li;

        else {
            if (arr[si] == num)
                return si;
            else
                return -1;
        }

    }