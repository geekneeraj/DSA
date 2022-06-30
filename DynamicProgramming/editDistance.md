# Edit Distance Problem

## We are allowed use these algorithm in following three cases:
* Insertion is allowed
* Deletion is allowed
* Replacement

``Note :`` Cost of all three steps mentioned above is O(1)

``Eg :`` Convert Cat to Cut ----> One step required { replacement }<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Convert Cast to Cat ------> One step required { deletion }<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Convert Cats to Cast ------> two steps required { deletion of last 's', insertion of 's' between 'a' and 't' }<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Convert Sunday to Saturday ------> three steps required { insertion of at, and replacement of n with r. }


## Program to find the edit distance

```C
#include<stdio.h>
#include<string.h>
int editDistance(char inp,char out)
{
    int dp[101][101];
    int m=strlen(inp);
    int m=strlen(out);
    dp[0][0]=0
    for(int i=0;i<n;i++)
    {
        dp[0][i]=dp[0][i-1]+1;
    }
    for(int j=0;j<m;j++)
    {
        dp[j][0]=dp[j-1][0]+1;
    }
    for(int i=1;i<=m;i++)
    {
        int q1=dp[i-1][j-1];// can be +1
        int q2=dp[i-1][j]; // can be +1
        int q3=dp[i][j-1]; // can be +1
        dp[i][j]=min(q1,min(q2,q3));
    }
    return dp[m][n];

}
int main()
{
    char inp[100],out[100];
    scanf("%s",inp);
    scanf("%s",out);

    int res=editDistance(inp,out);

    return 0;
}

```
## Time complexity calcuation

```
T(n)=Time taken to fill the box of m*n;
hence T(n) = O(m*n)

```
