# Dynamic Programming
## Fibonacci Number
0, 1, 1, 2, 3, 5, 8, 13

```
Equation for fibnacci number:

if(n==0)
fib(n)=0

if(n==1)
fib(n)=1

else 
fib(n)=fib(n-1)+fib(n-2)

```

```C
#include<stdio.h>

fib(int n)
{
if(n==0)
return 0;
else if(n==1)
return 1;

else
return fib(n-1)+fib(n-2);

}

int main()
{
int x=fib(10);
printf("%d",x);
return 0;
}
```

Analyzing the Complexity of the above program

```
                f(5) ---------------------------->  2^0
                /  \
               /    \
             f(4)   f(3) ------------------------>  2^1
             /\       /\   
            /  \     /  \
         f(3)   f(2)f(2) f(1) ------------------->  2^2
          /\     / \
         /  \   /   \
       f(2)f(1)f(1) f(0)------------------------->  2^3
       /\
      /  \
    f(1)  f(0) ----------------------------------->  2^4


Time complexity = a(r^n-1)/(r-1)
                = 1(2^n-1)/(2-1)
T(n)            = 2^n
```

## Using Memoization techniques to calculate Fibonacci number.

```C
#include<stdio.h>
int memo[1000];
fib(int n)
{
if(n==0)
return 0;
if(n==1)
return 1;

if(memo[n]==-1){
int num= fib(n-1)+fib(n-2);
memo[n]=num
return num

}
else
{
    return memo[n];
}

}

int main()
{
        for(int i=0;i<=10;i++)
        memo[i]=-1;

        int x=fib(10);
        printf("%d",x);
        return 0;
}

```
Calculation of Time complexity of the above program

```

+-----------------------------+
| -1 | -1 | -1 | -1 | -1 | -1 |
+-----------------------------+

 (5)
 /|\    +-------+      +------+
  |    \|/(2)   |     \|/(1)  |
f(5)-->f(4)-->f(3)-->f(2)-->f(1)-->f(0)
/|\(3)  |      /|\(1)   |    /|\ (0)  |
 +------+       +-------+     +-------+


f(5)=5

To fill one entery in array =  O(1)
-------------------of size n = O(n)

````