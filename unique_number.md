Editorial: 💡 Unique Number - I
X
Use property of xor function to solve this problem. Required Code is given below :


#include<iostream>
int main() {
    int t;
    cin >> t;

    int result = 0;
    while(t--){
        int n;
        cin >> n;
        result^=n;
    }
    cout << result << endl;
    return 0;
}
Lang - Java
Concept :

If we take XOR of zero and some bit, it will return that bit: a⊕0 = a
If we take XOR of two same bits, it will return 0: a⊕a=0
a⊕b⊕a = (a⊕a)⊕b = 0⊕b = b
So we can XOR all bits together to find the unique number.

public int singleNumber(int[] nums) {

        int val = 0;

        for(int i = 0;i < nums.length;i++){

            val = val ^ nums[i];
        }

        return val;
    }