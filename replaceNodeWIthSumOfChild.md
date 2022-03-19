# Replace Node with sum of child Node

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
	
void bfs(node * root)
	{
		std::queue<node*> q;
		q.push(root);
		while(!q.empty())
		{
			node * f=q.front();
			std::cout<<f->data<<",";
			q.pop();
			if(f->left)
			{
				q.push(f->left);
			}
			if(f->right)
			{
				q.push(f->right);
			}
		
		}
		
	return;

	}
	
//----------------------code to replace node with sum of child node---------------	
	int replaceSum(node * root)
	{
		if(root==NULL)
		{
			return 0;
		}
		if(root->left==NULL && root->right==NULL)
		{
			return root->data;
		
		}
		
		int leftsum=replaceSum(root->left);
		int rightsum=replaceSum(root->right);
		int temp=root->data;
		root->data=leftsum+rightsum;
		
		return temp+root->data;
	}
//------------------------------------------------------------------------------------	
int main()
	{
	node * t=buildTree();
	printTree(t);
	std::cout<<endl;
	replaceSum(t);
	std::cout<<endl;
	bfs(t);
	
	return 0;
	}


```
```
Input: 8 10 1 -1 -1 6 9 -1 -1 7 -1 -1 3 -1 14 13 -1 -1 -1

Output: 8 10 1 6 9 7 3 14 13 
    
        63,23,27,1,16,13,9,7,13,


```
