


```cpp
#include <iostream>
#include<bits/stdc++.h> 
#include<stack>
using namespace std;

int prec(char ch){
		if (ch == '^')
			return 3;
		else if (ch == '*' || ch == '/') {
			return 2;
		}
		else if (ch == '+' || ch == '-') {
			return 1;
		}
		return -1;
}
	
string infix_postfix(string s) {
	int l = s.length();
	//if (s.empty()) {
		//return s;
	//}
	stack<char> st;
	
	string new_str;
	for (int i = 0; i < l; i++)
	{
		if ((s[i] >= 'a' && s[i] <= 'z') || (s[i] >= 'A' && s[i] <= 'Z'))
			new_str += s[i];

		else if (s[i] == '(')
			st.push('(');

		else if (s[i] == ')') {
			while (!st.empty() && st.top() != '(') {
				new_str += st.top();
				st.pop();
			}
			if (st.top() == '(') {
				st.pop();
			}
		}

		else {
			while (!st.empty() && prec(s[i]) <= prec(st.top())) {
				new_str += st.top();
				st.pop();
			}
			st.push(s[i]);
		}
	}
		while (!st.empty()) {
			new_str += st.top();
			st.pop();
		}
	return new_str;
}
int main() {
	//code
	int ntc = 0;
	cin >> ntc;

	while (ntc--) {
		string str;
		cin >> str;
		cout << infix_postfix(str) << "\n";
	}

	return 0;
}
