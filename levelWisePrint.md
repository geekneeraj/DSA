# Level wise printing of nodes of a binary tree

In this section we will learn how to levelwise print node of binary tree in ``C++`` and ``Java``.

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
//---------------code for level wise printing--------------------	
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
void printKthLevel(node * root, int k)

{
	if(root==NULL)
	{
		return;
	}
	
	if(k==1)
	{
		cout<<root->data<<" ";
		return;
	}
	
	printKthLevel(root->left,k-1);
	printKthLevel(root->right,k-1);
}	
	
void levelWisePrint(node * root)

{
	int H=height(root);
	cout<<"heigth of tree= "<<H<<endl;

	for(int i=1;i<=H;i++)
	{
		printKthLevel(root,i);
		cout<<endl;
	
	}

	return ;

}
//-------------------------------------------------------	
int main()
	{
	node* t=buildTree();
	cout<<"printing tree"<<endl;
	printTree(t);
	cout<<endl;
	levelWisePrint(t);
	return 0;
	}

```

```
Input: 8 10 1 -1 -1 6 9 -1 -1 7 -1 -1 3 -1 14 13 -1 -1 -1

Output: printing tree
        8 10 1 6 9 7 3 14 13 
        heigth of tree= 4
        8 
        10 3 
        1 6 14 
        9 7 13

```