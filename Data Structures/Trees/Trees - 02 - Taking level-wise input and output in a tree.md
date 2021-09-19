### Taking level-wise input and output in a tree

I couldn't find any appropriate resource for performing this on youtube. If you find any dm me on [twitter](https://twitter.com/soulfulAutumn).

Traversing levelwise in an n-array tree - [Here](https://youtu.be/8r0jvz3hnzE)

Below is the implementation of the levelwise input and output. You must dry run it using either digital whiteboard or traditional pen-paper. If you don't do that, you won't get the gest of the code. Also try writing the code all by yourself after studying it once. I promise you will learn a lot.

```C++
#include <bits/stdc++.h>

using namespace std;

struct node{
	int data;
	vector <node*> children;
};

node* newNode (int key){
	node *temp = new node;
	temp -> data = key;
	return temp;
}

node* inputTree(){
	int rootData;
	cout << "Enter root data: ";
	cin >> rootData;
	node *root = newNode(rootData);

	queue <node*> pendingNodes;

	pendingNodes.push(root);
	while(pendingNodes.size() != 0){
		node *curr = pendingNodes.front();
		pendingNodes.pop();

		cout << "Enter number of children of " << curr -> data << ": ";
		int childrenNumber = 0;
		cin >> childrenNumber;
		for(int i = 0; i < childrenNumber; ++i){
			cout << "Enter the value of " << i << "th node of " << curr -> data << ": ";
			int k = 0;
			cin >> k;
			node *child = newNode(k);
			curr -> children.push_back(child);
			pendingNodes.push(child);
		}
	}
	return root;
}

void printTree(node* root){
	if(root == NULL)
		return;

	queue <node*> pendingNodes;
	pendingNodes.push(root);

	while(pendingNodes.size() != 0){
		node *curr = pendingNodes.front();
		pendingNodes.pop();

		cout << curr -> data << ": ";

		for(int i = 0; i < curr->children.size(); ++i){
			pendingNodes.push(curr -> children[i]);


 			cout << curr -> children[i] -> data << " ";

		}
		cout << endl;
	}
}


int main(){
	node *root = inputTree();
	cheatingPrint(root);
	printTree(root);
}
```
