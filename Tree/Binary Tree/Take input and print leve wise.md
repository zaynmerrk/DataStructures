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
BinaryTreeNode<int>* takeinputLevelWise() {
	int rootData;
	cout << "Enter rootData" << endl;
	cin >> rootData;

	if (rootData == -1)
		return NULL;

	BinaryTreeNode<int> *root = new BinaryTreeNode<int>(rootData);
	queue<BinaryTreeNode<int>*> pendingNodes;
	pendingNodes.push(root);

	while (pendingNodes.size() != 0) {
		BinaryTreeNode<int> *front = pendingNodes.front();
		pendingNodes.pop();

		int leftChildData;
		cout << "Enter leftChildData for" << front->data << endl;
		cin >> leftChildData;
		if (leftChildData != -1) {
			BinaryTreeNode<int> *leftChild = new BinaryTreeNode<int>(leftChildData);
			front->left = leftChild;
			pendingNodes.push(leftChild);
		}

		int rightChildData;
		cout << "Enter rightChildData for" << front->data << endl;
		cin >> rightChildData;
		if (rightChildData != -1) {
			BinaryTreeNode<int> *rightChild = new BinaryTreeNode<int>(rightChildData);
			front->right = rightChild;
			pendingNodes.push(rightChild);
		}
	}

	return root;
}
void printLevelWise(BinaryTreeNode<int> *root) {
	if (!root || root->data == -1)
		return;

	queue<BinaryTreeNode<int>*> pendingNodes;
	pendingNodes.push(root);

	while (pendingNodes.size()) {
		BinaryTreeNode<int> *front = pendingNodes.front();
		pendingNodes.pop();

		cout << front->data << ":";

		if (front->left) {
			cout << "L:" << front->left->data << ",";
			pendingNodes.push(front->left);
		}
		else {
			cout << "L:-1,";
		}

		if (front->right) {
			cout << "R:" << front->right->data << endl;
			pendingNodes.push(front->right);
		}
		else {
			cout << "R:-1" << endl;
		}

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

	BinaryTreeNode<int> *root = takeinputLevelWise();
	printLevelWise(root);



	/*||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||*/
	return 0;
}
/*^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^*/


template<typename T>
class BinaryTreeNode {
public:
	T data;
	BinaryTreeNode *left;
	BinaryTreeNode *right;

	BinaryTreeNode(T data) : data(data), left(NULL), right(NULL) { 
		// this->data = data;

	}

};











