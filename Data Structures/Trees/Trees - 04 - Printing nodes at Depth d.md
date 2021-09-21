### Printing nodes at depth d

Tutorial - Not found any tutorial on youtube. I found a tutorial which was on a level upper than this one. [Here](https://youtu.be/f-oTsCUCiXk). 

The only difference is that our target node is our root node.

Code:
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

int depthFlag = 0;

void nodesAtDepth(node * root, int d){
	if(d == 0){
		cout << root -> data << " ";
		depthFlag = 1;
	}

	for(int i = 0; i < root -> children.size(); ++i){
		nodesAtDepth(root -> children[i], d - 1);
	}
}

int main(){
	node *root = inputTree();
	printTree(root);
	cout << "Enter the level to be printed: ";
	int d = 0;
	cin >> d;
	cout << "Nodes at that depth are: ";
	nodesAtDepth(root, d);

	if(depthFlag == 0) cout << "No nodes present at given depth";
}
```