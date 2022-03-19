# Build Tree from Array

In this section we will learn how to build tree using array in ``C++`` and ``Java``.

```c

#include<stdio.h>
#include<stdlib.h>
#include<iostream>
#include<algorithm>
#include <queue>
using namespace std;
 
 
class node{
		public:
			int data;
			node * left;
			node* right;

		node(int d)
		{	
			data=d;
			left=NULL;
			right=NULL;
		}

	};
	
	
void printTree(node * root)
	{
		if(root==NULL)
		{
			return;
		}
		std::cout<<root->data<<" ";
		printTree(root->left);
		printTree(root->right);
	
	}
	
node * buildTreeFromArray(int *a, int s, int e)
	{
	
		if(s>e)
		{
			return NULL;
		
		}
		int mid=(s+e)/2;
		node * root=new node(a[mid]);
		root->left=buildTreeFromArray(a,s,mid-1);
		root->right=buildTreeFromArray(a,mid+1,e);
		return root;
	
	}
	
int main()
	{
	int a[]={1,2,3,4,5,6,7};
	int n=7;
	node * t=buildTreeFromArray(a,0,n-1);
	printTree(t);
	std::cout<<endl;
	return 0;
	}

```


```
Output: 4 2 1 3 6 5 7 

```