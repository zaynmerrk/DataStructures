``` cpp
Given a BST, convert it into a sorted linked list. You have to return the head of LL.

/*^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^*/

#define head first 
#define tail second 
#define nul NULL
pair<Node<int>*, Node<int>*> constructLinkedList_helper(BinaryTreeNode<int>* root) {
	pair<Node<int>*, Node<int>*> combinedList;

	if (!root) {
		pair<Node<int>*, Node<int>*> res;
		res.head = nul;
		res.tail = nul;
		return res;
	}

	pair<Node<int>*, Node<int>*> left = constructLinkedList_helper(root->left);
	pair<Node<int>*, Node<int>*> right = constructLinkedList_helper(root->right);

	Node<int>* newNode = new Node<int>(root->data);
    

	if (!left.head) {
		combinedList.head = newNode;
	}
	else {
		combinedList.head = left.head;
		left.tail->next = newNode;
	}

	//obvious
	newNode->next = right.head;

	if (!right.head) {
		combinedList.tail = newNode;
	}
	else {
		combinedList.tail = right.tail;
	}

	return combinedList;
}
Node<int>* constructLinkedList(BinaryTreeNode<int>* root) {
	return constructLinkedList_helper(root).head;
}
