
``` cpp
#include <iostream>
#include <string>
#include <vector>
using namespace std;

// use seperate directories for better understanding

int main() {
	Trie t;
	int n;
	cin >> n;
	string pattern;
	vector<string> vect;

	for (int i = 0; i < n; ++i) {
		string word;
		cin >> word;
		vect.push_back(word);
	}
	cin >> pattern;

	cout << (t.patternMatching(vect, pattern) ? "true" : "false");
}

#include "TrieNode.h"
#include <string>
#include <vector>
class TrieNode {
public :
	char data;
	TrieNode **children;
	bool isTerminal;

	TrieNode(char data) {
		this -> data = data;
		children = new TrieNode*[26];
		for (int i = 0; i < 26; i++) {
			children[i] = NULL;
		}
		isTerminal = false;
	}
};

class Trie {
	TrieNode *root;

public :
	int count;

	Trie() {
		this->count = 0;
		root = new TrieNode('\0');
	}

	bool insertWord(TrieNode *root, string word) {
		// Base case
		if (word.size() == 0) {
			if (!root->isTerminal) {
				root -> isTerminal = true;
				return true;
			} else {
				return false;
			}
		}

		// Small Calculation
		int index = word[0] - 'a';
		TrieNode *child;
		if (root -> children[index] != NULL) {
			child = root -> children[index];
		}
		else {
			child = new TrieNode(word[0]);
			root -> children[index] = child;
		}

		// Recursive call
		return insertWord(child, word.substr(1));
	}

	// For user
	void insertWord(string word) {
		if (insertWord(root, word)) {
			this->count++;
		}
	}

	bool search(TrieNode *root, string pattern) {
		if (!root)
			return 1;

		if (pattern.size() == 0) {
			return 1;
		}

		if (root->children[pattern[0] - 'a'] == NULL)
			return 0;


		return search(root->children[pattern[0] - 'a'], pattern.substr(1));

	}
	bool search(string pattern) {
		return search(root, pattern);
	}

	bool patternMatching(vector<string> vect, string pattern) {
		if (vect.size() == 0)
			return 0;

		for (int i = 0; i < vect.size(); i++) {
			string curr_string = vect[i];
			for (int j = 0; j < curr_string.size(); j++) {
				insertWord(curr_string.substr(j));
			}
		}

		return search(pattern);
	}
};
