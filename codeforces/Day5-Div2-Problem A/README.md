
### Description
* Problem A - Common Subsequence [https://codeforces.com/contest/1382/p...] <br>
* Contest Link : #658 [https://codeforces.com/contest/1384] <br>
* Youtube Video Explanation : https://www.youtube.com/watch?v=KoYbLscQIcQ <br>


### Question Explaination :
Find the Smallest Common non-empty Subsequence of two arrays A and B.

### Hint :
The smallest common subsequence will be obviously of length 1. So find any element which is common to both the arrays.
1.	Mark all elements present in array A using map.
2.	Iterate array B and check if the current element is already marked.
3.	If found any element, which is already marked, that will be the answer.

### Expected Complexity :
Time Complexity: O(NlogN)	//Insertion and access in map is logN.<br/>
Space Complexity: O(N)

### One of the Solution :
```cpp
#include<bits/stdc++.h>
#define ll      long long int
#define ld      long double
#define pll     pair<ll,ll>
#define vll     vector<ll>
#define pb      push_back
#define inf     1000000000000000000
#define endl    "\n"
#define MAX5    100005
#define MAX6    1000006
#define MOD     1000000007
#define nl      cout<<"\n"
#define fastIO  ios_base::sync_with_stdio(0);\
                cin.tie(NULL);\
                cout.tie(NULL)
using namespace std;

void solve() {
    ll n, m;
    cin >> n >> m;
    map<ll, bool> mp;
    for(ll i = 0 ; i < n ; i++) {
        ll x;
        cin >> x;
        mp[x] = true;
    }

    ll ans = -1;
    for(ll i = 0 ; i < m ; i++) {
        ll x;
        cin >> x;
        if(mp[x]) {
            ans = x;
        }
    }

    if(ans != -1) {
        cout << "YES" << endl;
        cout << 1 << ' ' << ans << endl;
    } else {
        cout << "NO" << endl;
    }

}

int main() {
    fastIO;

#ifndef ONLINE_JUDGE
    freopen("input.txt", "r", stdin);
#endif

    ll t = 1;
    cin >> t;
    while(t--)
        solve();

#ifndef ONLINE_JUDGE
    cout << endl << "Time Elapsed: " << 1.0 * clock() / CLOCKS_PER_SEC << " sec" << endl;
#endif

    return 0;
}
```
