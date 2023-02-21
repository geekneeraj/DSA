# Maximum sum sub array from given array.

```c++

#include<iostream.h>
using namespace std;

void main()
{

    int currentSum=0;
    int maximumSum=0;
    int n;
    cin>>n;

    int a[10];
    for (int i=0;i<n;i++)
    {
        a[i]=i;

    }

    //generate all sub array.

    for(int i=0;i<n;i++)
    {
        for(int j=1;j<n;j++)
        {
            currentSum=0;
            for(int k=i;k<=j;k++)
            {
                cout<<a[k]<<",";
                currentSum+=a[k];
            }
            maximumSum=currentSum>maximumSum?currentSum:maximumSum;
        }
    }
cout<<maximumSum;

}

```

------------------------------------End of Document--------------------------------