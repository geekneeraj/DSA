# Bottom Up Dynamic Programming

## Difference between DP and Memoization

```
                    Dynamic Programming
                            /\
                           /  \
                          /    \
                         /      \
                        /        \
                       /          \
                Top-Down       Bottom-Up
              (Memoization)    (Pure DP)

```


Bottom Up Dynamic programming

```C
Program to find nth fibonacci number using Bottom Up approach

#include<stdio.h>
int fibonacci(int n)
{
int dp[1000]={}
dp[0]=0;
dp[1]=1;
for(int i=2;i<=n;i++)
{
    dp[i]=dp[i-1]+dp[i-2];
}
return dp[n];
}

int main()
{
    printf("Enter the number");
    int n;
    scanf("%d",&n);
    printf("%d",fibonacci(n));
    return 0;
}

```