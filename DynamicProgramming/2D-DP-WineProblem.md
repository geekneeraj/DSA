# 2D-DP problem( Wine Problem )
## Problem Statement :
Given bottle of wines, maximum profit from a bottle that can be earned is priority of bottle * the year in which it was sold, given the condition that bottle can be sold from only one end.

```

      ||           ||         ||         ||
     /  \         /  \       /  \       /  \
    | 1  |       | 4  |     | 2  |     | 3  |
    |    |       |    |     |    |     |    |
    +----+       +----+     +----+     +----+
     (1)           (2)       (3)         (4)

     Maximum profit calculation:
     bottle (1) for the first year= 1*1
     bottle (4) for the second year= 2*3
     bottle (3) for the third year= 3*2
     bottle (2) for the fourth year= 4*4

     Total profit= 1+6+6+16= 29 


                    2,    3,   5,   1,   4
    Possibility 1: (2*1)(3*2)(5*5)(1*4)(4*3) Total Profit= 49 (selling least priority bottle earlier)
    Possibility 2: (2*1)(3*4)(5*5)(1*3)(4*2) Total profit= 50   

```

## Program to solve the above problem
```C
#include<stdio.h>
int maxProfit(int arr[],int be, int en, int year)
{
    if(be>en)
    return 0;
    int q1=arr[be]*year+maxProfit(arr,be+1, en,year+1); //sell from begining 
    int q2=arr[en]*year+maxProfit(arr,be,en-1,year+1); // sell from end

}
int main()
{
    int arr[100];
    int n; // no of bottles
    printf("%d",&n);
    for(int i=0;i<n;i++)
    scanf("%d",arr[i]); //prices of bottle

    int ans=maxProfit(arr,0,n-1,1);
    printf("%d",ans);

}

```

## Time complexity calculation
```
                B1 B2 B3 B4
                   /\
                  /  \
          (B1B2B3)   (B2B3B4)  

```