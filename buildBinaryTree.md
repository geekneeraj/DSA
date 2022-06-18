# Building binary tree

In this section we will learn how to build a binary tree in ``C++`` and ``Java``.


```c
#include<stdio.h>
#include<stdlib.h>
#include<iostream>

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
	
node* buildTree()
	{
		int d;
		std::cin>>d;
		node * root;
		if(d==-1)
		{
			return NULL;
		}
		root=new node(d);
		root->left=buildTree();
		root->right=buildTree();
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
	node * t=buildTree();
	printTree(t);
	return 0;
	}

```


```
Input:  3 4 -1 6 -1 -1
        5 1 -1 -1 -1

Output: 3 4 6 5 1

``` 
