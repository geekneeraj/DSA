# Checking whether a given binary tree is height balance tree or not

In this section we will learn check whether a tree is height balance tree or not using  ``C++`` and ``Java``.

```c

#include<stdio.h>
#include<stdlib.h>
#include<iostream>
#include<algorithm>
#include <queue>
 using namespace std;
 
class HBpair{
	public:
		int height;
		bool balance;

}; 
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
	
HBpair isHeightBalance(node * root)
	{
		HBpair p;
		if(root==NULL)
		{
			p.height=0;
			
			p.balance=true;
			return p;
			
		
		}
		HBpair left=isHeightBalance(root->left);
		HBpair right=isHeightBalance(root->right);
		p.height=max(left.height,right.height)+1;
		
		if(abs(left.height-right.height)<=1 && left.balance && right.balance)
		{
			p.balance=true;
			
		}
		else
		{
			p.balance=false;
		}
		
		return p;
		
	
	}
	
	
int main()
	{
	node * t=buildTree();
	printTree(t);
	std::cout<<endl;
	HBpair b=isHeightBalance(t);
	cout<<b.balance<<" ";
	std::cout<<endl;
	
	return 0;
	}

```


```
Input: 8 10 1 -1 -1 6 9 -1 -1 7 -1 -1 3 -1 14 13 -1 -1 -1

Output: 8 10 1 6 9 7 3 14 13 
        0

```