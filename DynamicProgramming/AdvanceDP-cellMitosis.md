# Cell Mitosis

## Problem Statement:
Given a cell, convert that cell into n cells, with following given conditions:
* Double the no of cells present in the container
* Increase the no of cells by 1 present in the container.
* Decrease the no of cells by 1 present in the container.

```C
Program for cell mitosis

#include<stdio.h>

long long solveCellProblem(int n, int x, int y, int z)
{
    long long dp[n+1];
    //Using bottom up dp here
    dp[0]=0;
    dp[1]=0;

    for(int i=2;i<=n;i++)
    {
        if(i%2==0)
        {
            dp[i]=min(dp[i/2]+x,dp[i-1]+y);
        }
        else
        {
            dp[i]=min(dp[i-1]+y,dp[(i+1)/2]+x+z);
        }
    }
    return dp[n];

}
int main()
{
    int n,x,y,z;
    scanf("%d%d%d%d",&n,&x,&y,&z);
    solveCellProblem(n,x,y,z);
    return 0;
}
```