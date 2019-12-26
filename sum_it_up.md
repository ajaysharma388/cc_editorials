Editorial: 💡 Sum It Up
X
Algorithm:

Sort the array(non-decreasing).
First remove all the duplicates from array.
Then use recursion and backtracking to solve the problem.
1. If at any time sub-problem sum == 0 then add that array to the result (vector of vectors).
2. Else if sum if negative then ignore that sub-problem.
3. Else insert the present array in that index to the current vector and call the function with sum = sum-ar[index] and index = index, then pop that element from current index (backtrack) and call the function with sum = sum and index = index+1


#include<bits/stdc++.h>
#include<unordered_set>
using namespace std;
 #define fio ios_base::sync_with_stdio(false)

#define ll long long int

#define s(x) scanf("%lld",&x)
#define s2(x,y) s(x)+s(y)
#define s3(x,y,z) s(x)+s(y)+s(z)

#define p(x) printf("%lld\n",x)
#define p2(x,y) p(x)+p(y)
#define p3(x,y,z) p(x)+p(y)+p(z)
#define F(i,a,b) for(ll i = (ll)(a); i <= (ll)(b); i++)
#define RF(i,a,b) for(ll i = (ll)(a); i >= (ll)(b); i--)

#define ff first
#define ss second
#define mp(x,y) make_pair(x,y)
#define pll pair<ll,ll>
#define pb push_back

ll inf = 1e18;
ll mod = 1e9 + 7 ;
ll gcd(ll a , ll b){return b==0?a:gcd(b,a%b);}

// TRY SOLVING IT AGAIN NEXT TIME AND MUST LOOK AT THE EDITORIAL  SOLUTION

vector<vector<int> >ans;
set<vector<int> > mp;
int B;

void solve(vector<int> &A,int i,int req,vector<int> st){
    if(i>A.size() or req<0)return ;

    if(req==0){
        if(!st.empty() and mp.find(st)==mp.end()){
            mp.insert(st);
            ans.push_back(st);
        }
    }

    if(i==A.size())return;

    st.push_back(A[i]);
    solve(A,i+1,req-A[i],st);
    st.pop_back();

    solve(A,i+1,req,st);

    vector<int> st2;
    st2.push_back(A[i]);
    solve(A,i+1,B-A[i],st2);
}


vector<vector<int> > combinationSum(vector<int> &A, int B) {
    ans.clear();
    mp.clear();
    ::B=B;
    if(A.size()==0 or B==0)return ans;
    sort(A.begin(),A.end());
    vector<int> st;
    solve(A,0,B,st);
    sort(ans.begin(),ans.end());
    return ans;
}

int main()
{
    // freopen("input.txt","r",stdin);
     freopen("output.txt","w",stdout);
    int t=1;
    //s(t);
    while(t--){
        int n;
        cin>>n;
        vector<int>ar(n);
        F(i,0,n-1)cin>>ar[i];
        int t;
        cin>>t;
        vector<vector<int>> ans = combinationSum(ar,t);
        for(auto vec:ans){
            for(int num:vec){
                cout<<num<<" ";
            }
            cout<<endl;
        }
    }
}
Algo
Sort the array to maintain the order of the provided answer and to remove duplicates i have checked the previous element as duplicacy will be because of the similar characters.

Lang - Java

public class Main {
    public static void main(String args[]) {

           Scanner scn = new Scanner(System.in);
        int n = scn.nextInt();
        int[] array = new int[n];

        for (int i = 0; i < array.length; i++) {
            array[i] = scn.nextInt();
        }

        int target = scn.nextInt();

        Arrays.sort(array);

        List> res = new ArrayList<>();
        helper2(array, 0, target, new ArrayList<>(), res);

        for(List each : res){

            for(int val : each){
                System.out.print(val+" ");
            }
            System.out.println();
    }
    }

    public static void helper2(int[] arr, int vidx, int target, List curr, List> res) {

        if (target == 0) {
            res.add(new ArrayList<>(curr));
            return;
        }

        if (target < 0) {
            return;
        }

        for (int i = vidx; i < arr.length; i++) {

            if (i == vidx || arr[i] != arr[i - 1]) {
                curr.add(arr[i]);
                helper2(arr, i + 1, target - arr[i], curr, res);
                curr.remove(curr.size() - 1);
            }
        }
    }

}