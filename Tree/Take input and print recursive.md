``` cpp
#include  <bits/stdc++.h>
#define MAX 1000
#define mod     1000000009
#define FIO     ios_base::sync_with_stdio(0); cin.tie(0); cout.tie(0)
#define nul     NULL
#define hell    INT_MIN
#define hevn    INT_MAX
#define ll     long long
#define  z "\n"
#include <iostream>
#include <vector>
#include <climits>
#define ff first
#define ss second
using namespace std;
#include "ComplexNumbers.h"
/*++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*/

TreeNode<int>* takeinput() {
	int data;
	cout << "Enter data" << endl;
	cin >> data;

	TreeNode<int> *root = new TreeNode<int>(data);

	cout << "Enter children size for data" << data << endl;
	int n;
	cin >> n;

	for (int i = 0; i < n; i++) {
		TreeNode<int> *child = takeinput();
		root->children.push_back(child);
	}

	return root;
}


void printTree(TreeNode<int>* root) {
	//edge case not base case
	if (!root)
		return;

	cout << root->data << ":";
	for (int i = 0; i < root->children.size(); i++) {
		cout << root->children[i]->data << ",";
	}

	cout << endl;

	for (int i = 0; i < root->children.size(); i++) {
		printTree(root->children[i]);
	}
}

/*^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^*/
int main() {
	/*||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||*/
#ifndef ONLINE_JUDGE
	freopen("input.txt", "r", stdin);
	freopen("output.txt", "w", stdout);
#endif
	/*||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||*/
	/*
	TreeNode<int> *root1 = new TreeNode<int>(1);
	TreeNode<int> *node1 = new TreeNode<int>(2);
	TreeNode<int> *node2 = new TreeNode<int>(3869);

	//let them connect
	root1->children.push_back(node1);
	root1->children.push_back(node2);
	printTree(root1);
	*/
	TreeNode<int> *root = takeinput();
	printTree(root);

	/*||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||*/
	return 0;
}



/*^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^*/
template<typename T>
class TreeNode {
public:
    T data;
    vector<TreeNode<T>*> children;

    TreeNode(T data) : data(data) {
        // this->data = data;
    }

};












