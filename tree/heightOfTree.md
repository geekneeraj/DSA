# Height of Binary Tree

In this section we will learn how to find height of binary tree in ``C++`` and ``Java``.

```c

#include<stdio.h>
#include<stdlib.h>
#include<iostream>
#include <algorithm>
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

//--------------Code to find height of Tree-----------------------------

int height(node * root)
	{
		if(root==NULL)
		{
			return 0;
		}
		int ls=height(root->left);		
		int rs=height(root->right);
		return std::max(ls,rs)+1;
	

	}

//------------------------------------------------

int main()
	{
	node* t=buildTree();
	cout<<"printing tree"<<endl;
	printTree(t);
	int h=height(t);
	std::cout<<"Height of tree= "<<h<<endl;
	return 0;
	}


```


```
Input:  8 10 1 -1 -1 6 9 -1 -1 7 -1 -1 3 -1 14 13 -1 -1 -1

Output: 8 10 1 6 9 7 3 14 13 Height of tree= 4

``` 


