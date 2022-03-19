# deleting a node in Binary Search Tree

In this section we will learn how to DELETE a node in Binary Search Tree using ``C++`` and ``Java``.


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
	
node * deleteInBST(node * root,int data)
	{
		if(root==NULL)
			return NULL;
		
		else if(data<root->data)
			{
				root->left=deleteInBST(root->left,data);
				return root;
			
			}
		else if(data==root->data)
			{
			
				if(root->left==NULL && root->right==NULL)
					{
						delete root;
						return NULL;
					
					}
				if(root->left!=NULL && root->right==NULL)
					{
						node * temp=root->left;
						delete root;
						return temp;
					
					}
				if(root->right!=NULL && root->left==NULL)
					{
						node * temp=root->right;
						delete root;
						return temp;
					
					}
				node * replace=root->right;
				
				while(replace->left!=NULL)
					{
						replace=replace->left;
						
					}
				
				root->data=replace->data;
				root->right=deleteInBST(root->right,replace->data);
				return root;
			
			}
			
		else
			{
				root->right=deleteInBST(root->right,data);
				return root;
			}
	
	
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
	cout<<endl;
	deleteInBST(t,2);
	cout<<endl;
	printTree(t);
	return 0;	
	}

```

```
Input: 1 2 3 4 5 9 8 7 6 -1

Output: 1 2 3 4 5 9 8 7 6 

        1 3 4 5 9 8 7 6
 
```