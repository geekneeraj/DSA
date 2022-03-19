# Flatten a Binary Search Tree

In this section we will learn how to flatten a Binary Search tree to linkedlist using ``C++`` and ``Java``.


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
class LinkedList
	{
		public:
			node * head;
			node * tail;
	
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
//----------code to flatten a bst-----------------------
LinkedList flatten(node * root)
	{
		LinkedList l;
		if(root==NULL)
			{
				l.head=l.tail=NULL;
				return l;
			}
		
		if(root->left==NULL && root->right==NULL)
			{
				l.head=l.tail=root;
				return l;
			}
		if(root->left!=NULL && root->right==NULL)
			{
				LinkedList leftLL=flatten(root->left);
				leftLL.tail->right=root;
				l.head=leftLL.head;
				l.tail=root;
				return l;
			}
		if(root->left==NULL && root->right!=NULL)
			{
				LinkedList rightLL=flatten(root->right);
				root->right=rightLL.head;
				l.head=root;
				l.tail=rightLL.tail;
				return l;
		
			}
		LinkedList leftLL=flatten(root->left);
		LinkedList rightLL=flatten(root->right);
		
		leftLL.tail->right=root;
		root->right=rightLL.head;
		l.head=leftLL.head;
		l.tail=rightLL.tail;
		return l;
	}
//-------------------------------------------------------------------	
int main()
	{
		node * t =build();
		printTree(t);
		cout<<endl;
		LinkedList l=flatten(t);
		node * temp=l.head;
		while(temp!=NULL)
			{
				cout<<temp->data<<"->";
				temp=temp->right;
			}
		cout<< endl;
	
	}

```

```
Input: 1 2 3 4 5 9 8 7 6 -1

Output: 1 2 3 4 5 9 8 7 6 
        1->2->3->4->5->6->7->8->9->
 
```