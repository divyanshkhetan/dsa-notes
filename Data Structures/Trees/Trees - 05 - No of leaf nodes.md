### Number of leaf nodes in a tree

This one is fairly simple. You will understand it with just one dryrun.

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

int leafNodes(node * root){
	if(root -> children.size() == 0)
		return 1;
	int ans = 0;

	for(int i = 0; i < root -> children.size(); ++i){
		ans += leafNodes(root -> children[i]);
	}

	return ans;
}

int main(){
	node *root = inputTree();
	printTree(root);
	cout << "No of leafs = " << leafNodes(root);
}
```