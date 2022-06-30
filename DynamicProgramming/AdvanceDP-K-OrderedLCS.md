# Mancunian and K ordeed LCS(Hacker earth)

## Program to solve the above problem

```C

#include<stdio.h>
#define ll long long
#define INF 1e9

ll n,m,a[2005],b[2005];
ll dp[2005][2005][8];
ll f(ll i,ll j,ll k)
{
    if(i==n||j==m)
    {
        // If any string is finished, ans is 0
        return 0;

    }
    //if the current state had already been computed
    if(i[j][k][k]!=-1)
    {
        return dp[i][j][k];
    }
    int res=0;
    if(a[i]==b[j])
    {
        res=1+f(i+1,j+1,k)
    }
    else
    {
        if(k>0){
        //we have converted a single  char to match with jth char of string b
        res=1+f(i+1,j+1,k-1);}
        res=max(res,f(i,j+1,k));

    }
    return dp[i][j][k]=res;
}

int main()
{
    memset(dp,-1,sizeof(dp));
    ll k;
    scanf("%d%d%d",m,n,k);
    f(i,0,n-1);
    scanf("%d",a[i]);
    f(i,0,m-1);
    scanf("%d",b[i]);

    ll ans=f(0,0,k);
    printf("%d",ans);


return 0;
}


```