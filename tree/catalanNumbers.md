# Catalan Numbers

###  In this session we will learn about Catalan Numbers.

## Binomial Coefficiant
 Binomial coefficiant <sup>n</sup>C<sub>k</sub> denotes the no of ways of selecting k items from n items.<br>
 C(n,r)=n!/(n-r)!*r!<br>
 Computing C(n,r) becomes very difficult when n and r are large. We may use DP or Pascal's triangle to compute some or all values of C(n,k).<br><br>
 C(n,r)=C(n-1,r)*C(n-1,k-1)<br>
 ```
 1
 1 1
 1 2 1
 1 3 3 1
 1 4 6 4 1
 1 5 10 10 5 1

 ```
 and so on Binomial Coefficiants are frequently used in problem solving.
 <br>

 ## Catalan Numbers

 How many ways are there to construct a Binary Search Tree with n nodes, which numbered from 1 to n.<br>
 <b>Hint: </b>Make every possibe i<sup>th</sup> node as root node and recursively count for no of BSTs. It, its left half and  right half. Do it for every value of i(1<=i<=n) and sum it up.<br>
 The formula generating after adding the series is the <b>Nth Catalan Number</b><br>
 It is defined using binomial coefficiant notation <sup>n</sup>C<sub>k</sup> as- <br>
 Cat(n)=<sup>2n</sup>C<sub>n</sub>/(n+1)<br>
Cat(0)=1<br>
Using the above formula, the first few terms of the series are -<br>
1, 1, 2, 5, 14, 42, 132, 429, 1430<br>

Another recursive formula is<br>
f(n)= <sup>i=n</sup> &#8721;<sub>i=1</sub> f(i-1)*f(n-i)<br>

## Applications of Catalan Numbers

* No of Possible binary tree with n nodes.
* No of expressions containing n pairs of parenthesis which are correctly matched.
* No of ways n+1 factors can be completely parenthesized for N.
* No of Unlabelled tree can be there with n nodes.
* No of paths with 2n steps on a rectengular grid from bottom left i.e from (n+1,0) to (0,n-1) thatdo not cross above the main diagonal.
* No of ways to form ``Mountain Ranges`` with n upstrokes and n downstrokes that all stay above the original line. Mountain range interpretation is that will never go below horizon.
```

N=0

*

No of ways=1

```

```
N=1

/\ 

No of Ways=1

```

```
N = 2
      /\
/\/\ /  \

No of ways = 2
```

```
N=3
                                       /\
          /\       /\        /\/\     /  \
/\/\/\ /\/  \     /  \/\    /    \   /    \

No of Ways = 5

```


## Program to find catalan no

```C
#include<stdio.h>
int catalan(int n)
{

    if(n==0)
    return 1;

    int ans=0;
    int i=0;
    for(i=0;i<=n;i++)
    {
        ans+=catalan(i-1)*catalan(n-1);
    }

    return ans;
}


int main()
{

    printf("%d",catalan(3));
    return 0;

}

````


```C
Using dynamic programming

#include<stdio.h>
int dp[100]={0}
int catalan(int n)
{

    if(n==0)
    return 1;

    if(dp[n]!=0)
    return dp[n];

    int ans=0;
    int i=0;
    for(i=0;i<=n;i++)
    {
        ans+=catalan(i-1)*catalan(n-1);
    }
    dp[n]=ans;
    return ans;
}


int main()
{

    printf("%d",catalan(3));
    return 0;

}

```