Editorial: 💡 Tower of Hanoi

Required recursive code is given below :


#include<iostream>
using namespace std;
void print(int ring,char x,char y){
    cout<<"Moving ring "<<ring<<" from "<<x<<" to "<<y<<endl;
}

//Function to shift rings from A to B using C.
void Procedure(int num,char from,char to,char helping,int top){
    if(num==1){
        print(top,from,to);
        return;
    }
    Procedure(num-1,from,helping,to,top);
    top=num;
    Procedure(1,from,to,helping,top);
    top=1;
    Procedure(num-1,helping,to,from,top);

}
int main() {
    int num;
    cin>>num;
    Procedure(num,'A','B','C',1);
}