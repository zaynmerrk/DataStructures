``` cpp
/*=======================================================================================================*/
class Node {
public:
    int data;
    Node *next, *prev;
    Node(int data) {
        this->data = data;
        next = nul;
        prev = nul;
    }
};
/*=======================================================================================================*/
// delete node at particular postion in doubly linked list
Node* deleteNode(Node *head, int pos) {
	if (!head)
		return nul;

	if (pos == 0) {
		Node *remove = head;
		head = head->next;
		head->prev = nul;
		delete(remove);
		return head;
	}

	int count = 0;
	Node *temp = head;
	while (temp && count < pos - 1) {
		count++;
		temp = temp->next;
	}


	if (temp && temp->next) {
		Node *remove = temp->next;
		temp->next = temp->next->next;
		delete(remove);
	}

	if (temp && temp->next) {
		temp->next->prev = temp;
	}


	return head;
}
/* -----------------------------------------------------------------------*/
// insert node at particular postion in doubly linked list
Node* insertNode(Node *head, int pos, int data) {
	if (!head)
		return nul;

	Node *newNode = new Node(data);

	if (pos == 0) {
		newNode->next = head;
		head->prev = newNode;
		return newNode;
	}

	int count = 0;
	Node* temp = head;
	while (count < pos - 1 && temp) {
		temp = temp->next;
		count++;
	}

	if (temp) {
		newNode->next = temp->next;
		temp->next = newNode;
		newNode->prev = temp;
	}

	if (newNode->next != NULL) {
		temp->next->prev = newNode;
	}

	return head;
}

/* -----------------------------------------------------------------------*/
//doubly linked list takeinput
Node* takeInput() {
	int data;
	cin >> data;

	Node *head = nul;
	Node *tail = nul;
	while (data != -1) {
		Node *newNode = new Node(data);
		if (head == nul) {
			head = newNode;
			tail = newNode;
		}
		else {
			tail->next = newNode;
			newNode->prev = tail;
			tail = newNode;
		}

		cin >> data;
	}
	return head;
}
/* -----------------------------------------------------------------------*/
void print(Node const  *head)   {
	Node const *temp = head;
	while (temp) {
		cout << temp->data << " ";
		temp = temp->next;
	}
}

/* -----------------------------------------------------------------------*/
int main() {
	/*||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||*/
#ifndef ONLINE_JUDGE
	freopen("input.txt", "r", stdin);
	freopen("output.txt", "w", stdout);
#endif
	/*||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||*/
	Node *head = takeInput();
	print(head);
	int i, data;
	cin >> i ;
	cout << "\n";
	head = deleteNode(head, i);
	print(head);


	/*||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||*/
	return 0;
}
