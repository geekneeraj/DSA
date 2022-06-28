# Minimum Steps required to Convert to one

## Allowed Steps:
* Divison by 3
* Divison by 2
* -1


Eg:<br>
21--(div by 3)--> 7--( -1 )-->6 --(div by 3)-->2--(div by 2)-->1 <br>
Total steps required= 4

## Program to find no of steps required to convert a no to 1

```C
#include<stdio.h>
int inf=1e9;
int memo[10000];// array for memoization
int reduceNo(int n)
{
    if(n==1) return 0;
    int q1=inf,q2=inf,q3=inf;

    if(memo[n]!=-1) return memo[n];// for memoization

    if(n%3==0) q1=1+reduceNo(n/3);
    if(n%2==0) q2=1+reduceNo(n/2);
    q3=1+reduceNo(n-1);
    memo[n]=min(q1,min(q2,q3));
    return min(q1,min(q2,q3));
}

int main()
{
    int n;
    // Loop is to initialize the memo value
    for(int i=0;i<=n;i++)
    {
        memo[i]=-1;
    }
    scanf("%d",&n);
    int ans=reduceNo(n);
    printf("%d",ans);
}

```

```C
DP solution

#include<stdio.h>
int reduceNoDP(int n)
{
    int dp[1000];
    dp[0]=0;
    dp[1]=1;
    dp[2]=1;
    dp[3]=1;

    //compute
    for(int i=0;i<=n;i++)
    {
        int q1=inf;
        int q2=inf;
        int q3=inf;
        if(dp[i]%3==0) q1=1+dp[i/3];
        if(dp[i]%2==0) q2=1+dp[i/2];
        else q3=1+dp[i-1];
        dp[i]=min(q1,min(q2,q3));

    }
    return dp[n];
}
int main()
{
    int n;
    // Loop is to initialize the memo value
    for(int i=0;i<=n;i++)
    {
        memo[i]=-1;
    }
    scanf("%d",&n);
    int ans=reduceNoDP(n);
    printf("%d",ans);
}


```


-------------------------------------------------------:End of Documents:--------------------------------------------------------