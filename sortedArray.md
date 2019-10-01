Required recursive code is given below :


#include<iostream>
using namespace std;
void Input(int arr[],int n){
    if(n==1){
        cin>>arr[0];
    }
    else{
        Input(arr,n-1);
        cin>>arr[n-1];
    }
}
bool Check(int arr[],int n) {
    if(n==1) return true;
    return arr[n-1]>=arr[n-2]&&Check(arr,n-1);
}
int main() {
    int arr[1000];
    int n;
    cin>>n;
    Input(arr,n);
    bool x=Check(arr,n);
    if(x) cout<<"true";
    else cout<<"false";
}