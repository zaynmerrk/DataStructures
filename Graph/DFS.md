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
//#include "ComplexNumbers.h"
/*++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*/

void printDFS(bool **edges, int n, int start, bool *visited) {
	cout << start << endl;
	visited[start] = 1;

	for (int i = 0; i < n; i++) {
		if (!visited[i] && edges[start][i]) {
			printDFS(edges, n, i, visited);
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

	printDFS(edges, n, 0, visited);
}
```
