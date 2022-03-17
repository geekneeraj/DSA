# Counting no of Nodes in a binary tree

In this section we will count no niodes in a binary tree using  ``C++`` and ``Java``.

```Counting

#include<stdio.h>
#include<stdlib.h>
#include<iostream>
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
//------------------code to count the no of nodes in a binary tree ---------------------
int count(node * root)
{
	if(root==NULL)
	{
		return 0;
	}
	return 1+count(root->left)+count(root->right);
	

}

//-------------------------------------------------------------------------------------	
int main()
	{
	node * t=buildTree();
	printTree(t);
	cout<<endl<<"no of nodes in tree= "<<count(t)<<endl;
	return 0;
	}


```

```
Input: 8 10 1 -1 -1 6 9 -1 -1 7 -1 -1 3 -1 14 13 -1 -1 -1

Output: 8 10 1 6 9 7 3 14 13 
        no of nodes in tree= 9

```