### Binary Trees

This is a very specific kind of tree and a very important one too. It is often asked in interviews and has many practical applications too.

In this kind of tree, each node can have either 0, 1 or 2 children but not more than that. A typical binary tree node looks like this:

```C++
struct node{
	int data;
	node* left;
	node* right;

	node(int key){
		data = key;
		left = NULL;
		right = NULL;struct node{
	int data;
	node* left;
	node* right;

	node(int key){
		data = key;
		left = NULL;
		right = NULL;
	}

	~node(){
		delete left;
		delete right;
	}
};
	}
};
```