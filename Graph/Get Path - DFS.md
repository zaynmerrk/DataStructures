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

vector<int>* getPath_DFS(bool **edge, int n, int start, int end, bool *visited) {
	if (start == end) {
		vector<int> *res = new vector<int>();
		res->push_back(end);
		return res;
	}

	visited[start] = 1;

	for (int i = 0; i < n; i++) {
		if (edge[i][start] && !visited[i]) {
			vector<int> *smallOutput = getPath_DFS(edge, n, i, end, visited);
			if (smallOutput != NULL) {
				smallOutput->push_back(start);
				return smallOutput;
			}
		}
	}
	return NULL;
}
int main() {
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

	int start, end;
	cin >> start >> end;

	vector<int> *output = getPath_DFS(edges, n, start, end, visited);

	if (output != NULL) {
		for (int i = 0; i < output->size(); i++) {
			cout << output->at(i) << " ";
		}
	}

	delete []visited;

	for (int i = 0; i < n; i++) {
		delete []edges[i];
	}

	delete []edges;
}

```
