# Checking a tree is Binary Search Tree or not

In this section we will learn how to check whether a tree is BST Or not using ``C++`` and ``Java``.


```c

#include<stdio.h>
#include<stdlib.h>
#include<iostream>
#include<algorithm>
#include <queue>
#include <climits>

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
	

bool isBST(node * root, int minV=INT_MIN, int maxV=INT_MAX)
	{
		if(root==NULL)
			return true;
		
		if(root->data>=minV && root->data<=maxV && isBST(root->left,minV,root->data) && isBST(root->right, root->data, maxV))
			return true;
		else
			return false;
		
	
	}	
	

	
int main()
	{
	node * t=buildTree();
	printTree(t);
	std::cout<<endl;
	if(isBST(t))
		cout<<"Yes";
	else
		cout<<"Not A BST";
	std::cout<<endl;	
	return 0;
	}

```

```
Input: 3 4 -1 6 -1 -1
       5 1 -1 -1 -1

Output: 3 4 6 5 1 
        Not A BST
 
```