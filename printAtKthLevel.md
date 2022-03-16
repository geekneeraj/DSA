# Print nodes at kth Level
In this section we will learn how to print node at kt level in ``C++`` and ``Java``.


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

//------------code to find node at kth level--------------	

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

//---------------------------------------------------------	
int main()
	{
	node* t=buildTree();
	cout<<"printing tree"<<endl;
	printTree(t);
	cout<<endl;
	}

```

```
Input: 8 10 1 -1 -1 6 9 -1 -1 7 -1 -1 3 -1 14 13 -1 -1 -1

Output: printing tree
        8 10 1 6 9 7 3 14 13 
        1 6 14
```