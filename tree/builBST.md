# Building Binary Search Tree

In this section we will learn how to build Binary Search Tree in ``C++`` and ``Java``.

```c

#include<stdio.h>
#include<stdlib.h>
#include<iostream>
#include<algorithm>
#include <queue>
using namespace std;

class node
	{
		public:
			int data;
			node * left;
			node * right;
			
			node(int d)
			{
				data=d;
				left=NULL;
				right=NULL;
				
			}
	};
	
node * insertInBST(node * root,int data)
	{
		if(root==NULL)
		{
			return new node(data);
		}
		
		if(data<=root->data)
		{
			root->left=insertInBST(root->left,data);
		}
	
		else
		{
			root->right=insertInBST(root->right,data);
		}
	
		return root;
	}
	
	node * build()
	{
		int d;
		cin>>d;
		node * root=NULL;
		while(d!=-1)
		{
			root=insertInBST(root,d);
			cin>>d;
		}
		
		return root;
	
	}
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
	
	
	int main()
	{
	node * t=build();
	printTree(t);
	return 0;	
	}

```


```
Input:  1 2 3 4 5 9 8 7 6 -1

OUtput: 1 2 3 4 5 9 8 7 6
```