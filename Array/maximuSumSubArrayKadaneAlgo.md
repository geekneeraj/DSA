# Kadane's Algorithm


```c++

#include<iostream>
using namespace std;
void main()
{
    int a[10];
    int currentSum=0;
    int maximumSum=0;

    for(int i=0;i<n;i++)
    {
        cin>>a[i];
    }

    //Kadane's Algrithm

    for(int i=0;i<n;i++)
    {
        currentSum+=a[i];
        if(currentSum<0)
            currentSum=0;

        maximumSum=Math.MAX(currentSum, maximumSum);
    }

    cout<<maximumSum;


}

```