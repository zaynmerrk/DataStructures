``` cpp
#include  <bits/stdc++.h>
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

/*++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*/

void printBFS(bool **edges, int n, int start, bool *visited) {
	queue<int> pendingVertices;
	pendingVertices.push(start);
	visited[start] = true;

	while (pendingVertices.size()) {
		auto front = pendingVertices.front();
		pendingVertices.pop();
		cout << front << " ";

		for (int i = 0; i < n; i++) {
			if (!visited[i] && edges[front][i]) {
				pendingVertices.push(i);
				visited[i] = 1;
			}
		}
	}
}

int main() {
	/*||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||*/
#ifndef ONLINE_JUDGE
	freopen("input.txt", "r", stdin);
	freopen("output.txt", "w", stdout);
#endif
	/*||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||*/
	int n, e;
	cin >> n >> e;
	bool **edges = new bool*[n];
	for (int i = 0; i < n; i++) {
		edges[i] = new bool[n];
		for (int j = 0; j < n; j++) {
			edges[i][j] = 0;
		}
	}


	//edges
	for (int i = 0; i < e; i++) {
		int f, s;
		cin >> f >> s;
		edges[f][s] = edges[s][f] = 1;
	}

	//visited array
	bool *visited = new bool[n];
	for (int i = 0; i < n; i++) {
		visited[i] = 0;
	}

	for (int i = 0; i < n; i++) {
		if (!visited[i])
			printBFS(edges, n, i, visited);
	}

	delete []visited;

	for (int i = 0; i < n; i++) {
		delete []edges[i];
	}

	delete []edges;
}
```
