# Cutting Rod problem

 Given the length of rod, and size of cut rod  with profit, how the rod should cut, so that maximum profit can be made.

```
 |--------|--------|--------|--------|
 
 |<------>|
 (profit: 2)
 |<--------------->|
        (profit: 3)
 |<------------------------>|
        (profit: 2)
 |<--------------------------------->|
        (profit: 5)

Profit calculation:
size(piece) profit
(3,1)----> 2+2=4
(2,2)----> 3+3=6
(2,1,1)--> 3+2+2=7
(1,1,1,1)-> 2+2+2+2=8
(4)-------> 5        

```

```C
Program to find the maximum profit

#include<stdio.h>
int maxProfit(int arr[],int totalLen)
{
    if(totalLen==0)
        return 0;
        int best=0;
    for(int len=1;len<=totalLen;len++)
    {
        int netProfit=arr[len]+maxProfit(arr,totalLen-len);
        best=max(best,netProfit);
    }
    return best;
}

int main()
{
    int priceOfEachLen[100];
    int totalLen;
    scanf("%d",totalLen);

    for(int eachPiece=1;eachPiece<=totalLen;eachPiece++)
    {
        scanf("%d",priceOfEachLen[eachPiece]);
    }
}


```

## Time complexity calculation of above code

```
for 4 len:
1 keep call 3 by recursion(for 3 len: 1 keep, 2 call by rec(1 keep 1 call by rec), 2 keep 1 call by rec)

2 keep call 2 by recursion(1 keep 1 call by rec)

3 keep call 1 by recursion

Above we can see that overlapping sub problems, hence here dp can be applied.

at each level in worst case, maximum possible branch=4

hence T(n)=O(4^n);

```

```C
Program to find the maximum profit using memoization

#include<stdio.h>
int memo[100];//memozation

int maxProfit(int arr[],int totalLen)
{
    if(totalLen==0)
        return 0;
        int best=0;

        if(memo[totalLen]!=-1)//memoization
        return memo[totalLen];//memoization

    for(int len=1;len<=totalLen;len++)
    {
        int netProfit=arr[len]+maxProfit(arr,totalLen-len);
        best=max(best,netProfit);
    }
    memo[totalLen]=best;//memoization
    return best;
}

int maxProfitBottomUp(int arr, int totalLen)
{
    if(totalLen==0)
        return 0;
    //intitalization of dp
    int dp[100]={0};

    for(int len=0;len<totalLen;len++)
    {
        int best=0;
        for(int cut=1;cut<=len;len++)
        {
            best=max(best,arr[cut]+dp[len-cut]);
        }  
        dp[len]=best     
    }

    return dp[totalLen];
}
int main()
{
    int priceOfEachLen[100];
    int totalLen;
    scanf("%d",totalLen);

    // Initialization of profit associated with each length
    for(int i=0;i<totalLen;i++)
    memo[i]=-1;

    for(int eachPiece=1;eachPiece<=totalLen;eachPiece++)
    {
        scanf("%d",priceOfEachLen[eachPiece]);
    }

    printf("%d",maxProfit(arr,totalLen));
    printf("%d",maxProfitBottomUp(arr, totalLen));
}


```

## Time complexity of the above program

```
Time taken fill  box1=Time to fill(1)=1
                                +
Time taken fill  box2=Time to fill(1,2)=2
                                +
Time taken fill  box3=Time to fill(1,2,3)=3
                                +
                    .
                    .
                    .
Time taken fill  box-n=Time to fill (1,2,3,4,5,6,7......n)=n
T(n)= 1+2+3+4+5+6+7+8+9+........n
    = O(n^2)

```