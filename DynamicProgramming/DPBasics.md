#  When to Use Dynamic Programming
While solving some problem if we found following two scenario, we can use DP to solve those problem.

* **Overlapping Sub problems :** When there are certain part of the program which is repeating again and again, that is  considered as overlapping sub problems.

* **Optimal substructure :** When local best is considered as the global best, then program can be considered having Optimal substructure.<br>
eg: 1---------------> 2----------------------> 3<br>
While travelling from 1 to 3 with min distance, then distance from 1 to 2(say 30, 40 it is mandatory to take 30) should be minimum as well distance from 2 to 3(say 50, 60 then mandatory to take 50) should be minimum.<br>



```C
#include<stdio.h>

int minCost(int grid[][100],int m, int n)
{
    int dp[100][100];
    dp[0][0]=grid[0][0];

    for(int c=1;c<n;c++){dp[0][c]=dp[0][c-1]+grid[0][c];}

    for(int r=1;r<m;r++){dp[0][r-1]=dp[0][c-1]+grid[r][0];}

    for(int r=1;r<m;r++)
    for(int c=1;c<n;c++)
    {
        dp[r][c]=min(dp[r-1][c],dp[r][c-1]);
    }
return dp[m-1][n-1];
}

int main()
{
    int grid[100][100]={
        {1,2,3},
        {4,8,2},
        {1,5,3}

    }
    int ans=minCost(grid,3,3);
    printf("%d",ans);

    return 0;
}

```
## Time Complexity
```
Since we are filling the grid of m*n,
hence T(n)=(m*n)
```


---------------------------------------------------------------: End of Document :---------------------------------------------------------------