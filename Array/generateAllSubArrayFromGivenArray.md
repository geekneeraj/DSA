# Generate all sub array from the given array.

* If an subarray of array start at index i and end at index j and i to j are continious are called continious sub array.

```c++
#include<iostream.h>
using namespace std;

void main()
{
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
            for(int k=i;k<=j;k++)
            {
                cout<<a[k]<<",";
            }
            cout<<endl;
        }
    }


}

```




-------------------------------End of Document-------------------------------