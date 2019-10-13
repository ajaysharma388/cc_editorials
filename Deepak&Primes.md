Editorial: 💡 Deepak and Primes
X
The problem can be easily solved by using Sieve of Eratosthenes. We just need to precompute the sieve and then run our loop for all the test cases and answer all the queries. All the queries will be answered in O(1) complexity as we have already precomputed the sieve for extracting prime numbers.


/*input
8
1
10
100
1000
10000
100000
1000000
5000000
*/
#include <bits/stdc++.h>
using namespace std;

#define boost  ios_base::sync_with_stdio(false);
#define endl '\n'
#define mp make_pair
#define pb push_back
#define ppb pop_back
#define fi first
#define se second
#define ll long long
#define ull unsigned long long
#define pii pair<ll, ll>
#define f(i,a,b) for(ll i = (ll)(a); i <= (ll)(b); i++)
#define rf(i,a,b) for(ll i = (ll)(a); i >= (ll)(b); i--)
#define ms(a,b) memset((a),(b),sizeof(a))
#define max(a,b) ((a>b)?(a):(b))
#define min(a,b) ((a<b)?(a):(b))

#define abs(x) ((x<0)?(-(x)):(x))
#define MAX 100005
#define inf LLONG_MAX
#define MIN INT_MIN

//typedef
typedef pair<int, int> ii;
typedef vector<ii> vii;
typedef vector<vii> vvii;

int mod = 1e9 + 7 ;
ll gcd(ll a , ll b){return b==0?a:gcd(b,a%b);}
ll powmod(ll a,ll b) {ll res=1;if(a>=mod)a%=mod;for(;b;b>>=1){if(b&1)res=res*a;if(res>=mod)res%=mod;a=a*a;if(a>=mod)a%=mod;}return res;}

/*..................................................................................................................................*/
bool v[100000005];
//ll sp[5000005];
vector<int>prime_vector;
void Sieve()
{
    for(ll i = 2; i < 100000005; i += 2)  
       {
       //even numbers have smallest prime factor 2
        v[i]=true;
        //sp[i]=2;
       } 
         prime_vector.pb(2);
    for (ll i = 3; i < 100000005; i += 2)
    {
        if (!v[i])
        {   prime_vector.pb(i);
            for (ll j = i; (j*i) < 100000005; j += 2)
            {
                if (!v[j*i])    
                    v[j*i] = true;//sp[i*j]=i;
            }
        }
    }
}

int main() 
{
   ios_base::sync_with_stdio(false);cin.tie(0);
   int t;cin>>t;
   int k;
   Sieve();
   while(t--)
   {
    cin>>k;
    k--;
    cout<<prime_vector[k]<<endl;
   }
   return 0;
}

Lang - Java
Following is the algorithm to find all the prime numbers less than or equal to a given integer n by Eratosthenes’ method:

Create a list of consecutive integers from 2 to n: (2, 3, 4, …, n).
Initially, let p equal 2, the first prime number.
Starting from p2, count up in increments of p and mark each of these numbers greater than or equal to p2 itself in the list.
These numbers will be p(p+1), p(p+2), p(p+3), etc..
Find the first number greater than p in the list that is not marked.
If there was no such number, stop. Otherwise, let p now equal this number (which is the next prime), and repeat from step 3.


  public static int soe(int n) {
        boolean[] primes = new boolean[1_000_000_05];

        Arrays.fill(primes, true);

        primes[0] = false;
        primes[1] = false;

        for (int table = 2; table * table <1_000_000_05; table++) {
            if (primes[table]) {
                for (int mult = 2; table * mult <1_000_000_05; mult++) {
                    primes[table * mult] = false;
                }
            }
        }

        int cnt = 0;

        for (int i = 2; i < primes.length; i++) {

            if (primes[i]) {
                cnt++;
            }

            if (cnt == n) {
                return i;
            }
        }
            // System.out.println(cnt);
        return n;
    }