### Description
* Problem D - Berserk And Fireballs [https://codeforces.com/contest/1380/p...] <br>
* Contest Link : https://codeforces.com/contest/1380 <br>
* Youtube Video Explanation : https://www.youtube.com/watch?v=8PFh4gSRO5M <br>


### Question Explaination :
There are 𝑛 warriors in a row having pairwise distinct power as 𝑎𝑖
You have two types of spells which you may cast:
Fireball: you spend 𝑥 mana and destroy exactly 𝑘 consecutive warriors;
Berserk: you spend 𝑦 mana, choose two consecutive warriors and the warrior with greater power destroys another chosen warrior.
To turn the current sequence of warriors powers 𝑎1,𝑎2,…,𝑎𝑛 into 𝑏1,𝑏2,…,𝑏𝑚. find the minimum amount of mana needed.

### Hint :
The first thing we need to do is to find the occurrence of b in array a. These are the monsters that are needed to be present. Now in between these monsters what are the segments are there we need to treat them separately.
Superhit segment there can be two possibilities. 
First being if the monsters that need to be remain have the their maximum value greater than the maximum value in the segment. In this case what we can do is we can simply use the second spell and detect y*number of elements in the segment or x into number of sub segments of key length + the remaining*y add the minimum of the above 2 into the answer.
2nd cases when the maximum neighbouring element is less than the maximum segment value. In this case what we have we can do is wehave to subtract a self assessment of kill and using the fireball spell if that's not possible the answer is -1 else what we can do is, find the minimum (of x + y*segment length-k, x*(no. of sub segment of size k) + y* remaining elements).

### Expected Complexity :
Time Complexity O(N) and Space O(N)

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
    long long n, m;
    cin>>n>>m;
    long long x,k,y;
    cin>>x>>k>>y;
    long long a[n], b[m];
    for (long long i = 0; i < n; ++i)
    {
        cin>>a[i];
    }
    for (long long i = 0; i < m; ++i)
    {
        cin>>b[i];
    }
    if(n == 1)
    {
        cout<<0<<endl;
        return 0;
    }
    long long in = 0;
    long long c[n] = {0};
    for (long long i = 0; i < n; ++i)
    {
        if(a[i] == b[in])
        {
            c[i] = 0;
            in++;
        }
        else{
            c[i] = 1;
        }
    }
    if(in != m)
    {
        cout<<-1<<endl;
        return 0;
    }
    long long marker = 1;
    for (long long i = 0; i < n-1; ++i)
    {
        if(c[i] == 0 && c[i+1] == 1)
        {
            marker++;
        } 
        if(c[i] == 1)
            c[i] = marker;
    }
    if(c[n-1] == 1)
        c[n-1] = marker;
    vector< long long > v[n+5];
    for (long long i = 0; i < n; ++i)
    {
        v[c[i]].push_back(a[i]);
    }
    long long max_neighbour[n+5] = {0};
    for (long long i = 1; i < n-1; ++i)
    {
        if(c[i-1] == 0 && c[i] != 0)
        {
            max_neighbour[c[i]]=max(max_neighbour[c[i]], a[i-1]);
        }
        if(c[i+1] == 0 && c[i] != 0)
        {
            max_neighbour[c[i]]=max(max_neighbour[c[i]], a[i+1]);
        }
    }
    if(c[n-1] != 0 && c[n-2] == 0)
    {
        max_neighbour[c[n-1]] = a[n-2];
    }
    if(c[0] != 0 && c[1] == 0)
    {
        max_neighbour[c[0]] = a[1];
    }
    long long max_ele[n+5]={0};
    for (long long i = 0; i < n+5; ++i)
    {
        for (long long j = 0; j < v[i].size(); ++j)
        {
            max_ele[i] = max(max_ele[i], v[i][j]);
        }
    }
    long long ans = 0;
    for (long long i = 1; i < n+5; ++i)
    {
        if(max_ele[i] > max_neighbour[i])
        {
            if(v[i].size()<k)
            {
                cout<<-1;
                return 0;
            }
            ans += min(v[i].size()%k * y + v[i].size()/k * x, x + (v[i].size()-k)*y);
        }
        else{
            ans += min(v[i].size() * y, v[i].size()/k * x + v[i].size()%k * y);
        }
    }
    cout<<ans<<endl;
}
```
