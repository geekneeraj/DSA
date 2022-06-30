# Longest Increasing susequence

```C
#include<stdio.h>
int lis(int arr[100],int n)
{
    int dp[100];
    for(int i=0;i<n;i++)dp[i]=1;
    int best=-1;
    for(int i=1;i<n;i++)
    {
        
        for(int j=0;j<i;j++)
        {
        if(arr[j]<=arr[i])
        {
           //jth element can be absorbed by ith element 
           int curLen=1+dp[j];
           dp[i]=max(curLen,dp[i]);
        }
        }
        best= max(best,dp[i]);
    }
   return best;
}

int main()
{
    int arr[100];
    int n;
    scanf("%d",&n);
    for(int i=0;i<n;i++)
    {
        scanf("%d",arr[i]);
        
    }
    int ans=lis(arr,n);
    printf("%d",ans);
    return 0;
}

```