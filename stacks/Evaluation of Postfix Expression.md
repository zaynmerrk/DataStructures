``` cpp
#include <iostream>
#include <bits/stdc++.h>
#include<stack>
using namespace std;
bool number(char c) {
	return c != '/' && c != '*' && c != '+' && c != '-';
}

int evaluate_postfix(string s) {
	int n = s.length();
	if (!n)
		return -1;

	stack<int> st;
	for (int i = 0; i < n; i++) {
		if (number(s[i])) {
			st.push(s[i] - '0');
		}
		else {
			int val1 =  st.top(); 
			st.pop();
			int val2 = st.top(); 
			st.pop();
				switch (s[i]) {
				case '+' : st.push(int(val1 + val2)); break;
				case '-' : st.push(int(val2 - val1)); break;
				case '*' : st.push(int(val1 * val2)); break;
				case '/' : st.push(int(val2 / val1)); break;
			}
		}
	}
	return st.top();
}

int main() {
	//code
	int ntc;
	cin >> ntc;

	while (ntc--) {
		string str;
		cin >> str;
		cout << evaluate_postfix(str) << "\n";
	}

	return 0;
}
