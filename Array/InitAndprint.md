# Steps to initialize and print array element.


```C++
#include<iostream>
using namespace std;

void main()
{
int a[10];
for(int i=0;i<=9;i++)
{

    cout<<a[i]; //print grabage value
}
a[10]={2};

//print first element as 2 and remaining as 0
for(int i=0;i<=9;i++)
{

    cout<<a[i]; 
}
a[10]={2,3,4};
//print element as 2 3 4 and remaining as 0
for(int i=0;i<=9;i++)
{

    cout<<a[i]; 
}
//print in reverse order

for(int i=0;i<=9;i++)
{

    cout<<a[9-i]; 
}

}


```

---------------------------End of Document-----------------------