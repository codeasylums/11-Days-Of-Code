
### Description
* Problem A - Three Indices [https://codeforces.com/contest/1380/problem/A] <br>
* Contest Link : https://codeforces.com/contest/1380  <br>
* Youtube Video Explanation : https://www.youtube.com/watch?v=SRXDhea2b0A <br>


### Question Explaination :
For 3 indices i, j and k of an array, find any set of i, j and k where a[ j ] > a[ i ] and a[ j ] > a[ k ]

Condition : i < j < k

### Hint :
Finding any of the mountain peak


### Expected Complexity :
Time Complexity  : O (n)

### One of the Solution :
```cpp
#include<bits/stdc++.h>
using namespace std;
int main()
{
        #ifndef ONLINE_JUDGE
            freopen("input.txt","r",stdin);
            freopen("output.txt","w",stdout);
        #endif
 
    int t;
    cin>>t;
    while(t--)
    {
        int n;
        cin>>n;
        int a[n];
        for (int i = 0; i < n; ++i)
        {
            cin>>a[i];
        }
        bool is_yes = false;
        for (int j = 1; j < n-1; ++j)
        {
            if(a[j-1] < a[j] && a[j] > a[j+1])
            {
                is_yes = true;
                cout<<"YES\n";
                cout<< j <<" "<< j+1<<" "<< j+2 <<endl;
                break;
            }
        }
        if(!is_yes)
        {
            cout<<"NO\n";
        }
        
    }
 
}
```
