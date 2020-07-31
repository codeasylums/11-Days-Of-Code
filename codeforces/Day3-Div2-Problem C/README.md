
### Description
* Problem C - Create The Teams [https://codeforces.com/contest/1380/p...] <br>
* Contest Link : https://codeforces.com/contest/1380  <br>
* Youtube Video Explanation : https://www.youtube.com/watch?v=jwC6PVU6gOI <br>


### Question Explaination :
You are given an array where he stands for the programmers skills and you have to form teams such that the number of team members x the minimum skill in the team is greater than equal to x and we have to maximise the number of teams.

### Hint :
To maximize the number of teams what you can do is firstly sort the array and then starting from the maximum element check whether placing that element in the current team would make the the team satisfy the condition such that the number of team members x the meaning skill is greater than equal to x. If that is not true we can go on and choose the next greatest element and add it to the same team but if adding the current programmer mix 13 satisfy the conditions we leave the team with that only and we can try to make a new team.

### Expected Complexity :
time complexity O(Nlog(N)) and space complexity is O(N).

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
        int x;
        cin>>x;
        int a[n];
        for (int i = 0; i < n; ++i)
        {
            cin>>a[i];
        }
        sort(a,a+n);
        reverse(a,a+n);
        int ans = 0;
        int count = 0;
        for (int i = 0; i < n; ++i)
        {
            count++;
            if(a[i]*count >= x)
            {
                count = 0;
                ans++;
            }
        }
        cout<<ans<<endl;
    }
}
```
