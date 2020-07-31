
### Description
* Problem B - Universal Solution [https://codeforces.com/contest/1380/p...] <br>
* Contest Link : https://codeforces.com/contest/1380 <br>
* Youtube Video Explanation : https://www.youtube.com/watch?v=rdrNmiJuhdE <br>


### Question Explaination :
Bot has a string 𝑠=𝑠1𝑠2…𝑠𝑛 of length 𝑛 where each letter is either R, S or P. [R=Rock, P=Paper, S=Scissor]
In the first round, he chooses "Rock", "Scissors" or "Paper" based on the value of 𝑠𝑝𝑜𝑠, the second round, the bot's choice is based on the value of 𝑠𝑝𝑜𝑠+1. In the third round — on 𝑠𝑝𝑜𝑠+2 and so on. After 𝑠𝑛 the bot returns to 𝑠1 and continues his game.
Let your choices are 𝑐1𝑐2…𝑐𝑛 and if the bot starts from index 𝑝𝑜𝑠 then you'll win in 𝑤𝑖𝑛(𝑝𝑜𝑠) rounds. Find 𝑐1𝑐2…𝑐𝑛 such that 
(𝑤𝑖𝑛(1)+𝑤𝑖𝑛(2)+⋯+𝑤𝑖𝑛(𝑛)) / 𝑛 is maximum possible.



### Hint :
Let's see the contribution of individual choice in the the string provided by us. For every ci we can come up with the wins 
Let's look at the contribution of each choice ci to the total number of wins win(1)+win(2)+⋯+win(n) (we can look at "total" instead of "average", since "average" is equal to "total" divided by n). For example, let's look at the first choice c1: in win(1) we compare c1 with s1, in win(2) — c1 with s2, in win(3) — c1 with s3 and so on.

In the result, we compare c1 with all si once. So, to maximise the total sum, we need to choose c1 that beats the maximum number of si or, in other words, let's find the most frequent character in s and choose c1 that beats it.

Okay, we found the optimal c1.can we can send like this for every ci because the contribution for each is same as that of ci so it doesn't matter what index we are using. Just need to check for an individual index what is the maximum we can get for that index and copy that for all other ci.


### Expected Complexity :
Complexity : The time complexity is O(n) and space is O(1).

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
        string s;
        cin>>s;
        int R=0, P=0, S=0;
        for (int i = 0; i < s.length(); ++i)
        {
            if(s[i] == 'R')
                R++;
            if(s[i] == 'P')
                P++;
            if(s[i] == 'S')
                S++;
        }
        if(R >= P && R >= S)
        {
            for (int i = 0; i < s.length(); ++i)
            {
                cout<<'P';
            }
            cout<<endl;
            continue;
        }
        if(P >= S && P >= S)
        {
            for (int i = 0; i < s.length(); ++i)
            {
                cout<<'S';
            }
            cout<<endl;
            continue;
        }
        if(S >= P && S >= R)
        {
            for (int i = 0; i < s.length(); ++i)
            {
                cout<<'R';
            }
            cout<<endl;
            continue;
        }
    }
}
```
