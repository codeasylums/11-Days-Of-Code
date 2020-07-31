
### Description
* Problem C - Prefix Flip (Hard Version)[https://codeforces.com/contest/1382/p...] <br>
* Contest Link : #658 [https://codeforces.com/contest/1382] <br>
* Youtube Video Explanation : https://www.youtube.com/watch?v=YUdUOAZx7mo <br>


### Question Explaination :


### Hint :


### Expected Complexity :


### One of the Solution :
```cpp
/**
        *AUTHOR:Mayank Padia*
        *Birla Institute of Technology,Mesra*    
**/
#include<bits/stdc++.h>
typedef long long ll;
typedef double ld;
#define vll vector<ll>
#define vvll vector< vll >
#define vld vector< ld >
#define vvld vector< vld >
#define pll pair<ll ,ll >
#define vllp vector< pll >
#define mp make_pair
#define pb push_back
#define MOD 1000000007
#define endl "\n"
#define test ll t;cin>>t;while(t--)
#define all(v) v.begin(),v.end()
#define rall(v) v.rbegin(),v.rend()
#define F first
#define S second
#define MAX 1000000007
#define cf_MOD 998244353
#define forn(i,n) for(ll (i) = 0 ; (i) < (n) ; ++(i))
#define for1(i,n) for(ll (i) = 1 ; (i) <= (n) ; ++(i))
#define forr(i,n) for(ll (i) = (n)-1 ; (i)>=0 ; --(i))
#define forab(i,a,b,c) for(ll (i) = a ; (i) <= (b) ; (i)+=(c))
#define trace1(x)                cerr<<#x<<": "<<x<<endl
#define trace2(x, y)             cerr<<#x<<": "<<x<<" | "<<#y<<": "<<y<<endl
#define trace3(x, y, z)          cerr<<#x<<":" <<x<<" | "<<#y<<": "<<y<<" | "<<#z<<": "<<z<<endl
#define trace4(a, b, c, d)       cerr<<#a<<": "<<a<<" | "<<#b<<": "<<b<<" | "<<#c<<": "<<c<<" | "<<#d<<": "<<d<<endl
#define trace5(a, b, c, d, e)    cerr<<#a<<": "<<a<<" | "<<#b<<": "<<b<<" | "<<#c<<": "<<c<<" | "<<#d<<": "<<d<<" | "<<#e<< ": "<<e<<endl
#define trace6(a, b, c, d, e, f) cerr<<#a<<": "<<a<<" | "<<#b<<": "<<b<<" | "<<#c<<": "<<c<<" | "<<#d<<": "<<d<<" | "<<#e<< ": "<<e<<" | "<<#f<<": "<<f<<endl
 
using namespace std;
 
vll sieve;
void Sieve(int N){
    const ll maxn = N;
    sieve.resize(maxn);
    forn(i,maxn) sieve[i] = i;
    sieve[1] = -1;
    sieve[0] = -1;
    forab(i,2,maxn,1) if(i == sieve[i]) for(ll j = 2*i ; j < maxn ; j+=i) if(sieve[j] == j) sieve[j] = i;
}
ll extended_GCD(ll a , ll b , ll &x , ll &y){
    if(a == 0){
        x = 0;
        y = 1;
        return b;
    }
    ll x1 , y1;
    ll gcd = extended_GCD(b%a , a , x1 , y1);
    x = y1 - (b/a)*x1; 
    y = x1;
    return gcd;
}
ll power(ll a, ll b, ll m = MOD) {
    a %= m;
    ll res = 1;
    while (b > 0) {
        if (b & 1)
            res = res * a % m;
        a = a * a % m;
        b >>= 1;
    }
    return res;
}
ll modinv(ll a , ll mod = MOD){
    ll x , y;
    extended_GCD(a , mod , x , y);
    if(x < 0) x += mod;
    return x;
}
//s=bitset<64>(val).to_string();
///////////////////////////////////////////////////////////////////////
 
 
void solve(){
    ll n;
 
    //memset(a,-1,sizeof(a));
    cin>>n;
    string a, b;
    cin>> a >> b;
    vector<ll> operations;
    for (int i = 0; i < n-1; ++i)
     {
         if(a[i] != a[i + 1])
            operations.push_back(i + 1);
     } 
     if(a[n - 1] == '1')
        operations.push_back(n);
    ll in = -1;
    for (int i = n-1; i >= 0; --i)
    {
        if(b[i] == '1'){
            operations.push_back(i + 1);
            in = i;
            break;}
    }
    for (int i = in-1; i >= 0; --i)
    {
        if(b[i] != b[i+1])
        {
            operations.push_back(i + 1);
        }
    }
    cout<<operations.size()<<" ";
    for(auto it : operations)
    {
        cout<<it<<" ";
    }
    cout<<endl;
    
    
    }
    
int main(){
        #ifndef ONLINE_JUDGE
            freopen("input.txt","r",stdin);
            freopen("output.txt","w",stdout);
        #endif
    ios::sync_with_stdio(0); cin.tie(0);
    int t=1;
    cin>>t;
    while(t--){
        solve();
    }
    #ifndef ONLINE_JUDGE
        cout<<"\nTime Elapsed : " << 1.0*clock() / CLOCKS_PER_SEC << " s\n";
    #endif
return 0;
}

```
