``` cpp
#include <bits/stdc++.h>
using namespace std;

void printDFS(bool **edges, int n, int start, bool *visited, vector<int> *res) {
	res->push_back(start);
	visited[start] = 1;

	for (int i = 0; i < n; i++) {
		if (!visited[i] && edges[start][i]) {
			printDFS(edges, n, i, visited,res);
		}
	}
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

	vector<int> *res = new vector<int>;
	for (int i = 0; i < n; i++)
	{
		if (!visited[i])
		{
			printDFS(edges, n, i, visited, res);
		}
		sort(res->begin(), res->end());
		for (int i = 0; i < res -> size(); i++)
		{
			cout << res -> at(i) << " ";
		}
		res->clear();
		cout << endl;
	}

	return 0;
}

/*^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^*/ //using BFS

void printBFS(bool **edges, int n, int start, bool *visited, vector<int> *res) {
	queue<int> pendingVertices;
	pendingVertices.push(start);
	visited[start] = 1;
	res->push_back(start);

	while (pendingVertices.size()) {
		auto front = pendingVertices.front();
		pendingVertices.pop();

		for (int i = 0; i < n; i++) {
			if (!visited[i] && edges[i][front]) {
				pendingVertices.push(i);
				visited[i] = 1;
				res->push_back(i);
			}
		}
	}
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

	vector<int> *res = new vector<int>;
	for (int i = 0; i < n; i++)
	{
		if (!visited[i])
		{
			printBFS(edges, n, i, visited, res);
		}
		sort(res->begin(), res->end());
		for (int i = 0; i < res -> size(); i++)
		{
			cout << res -> at(i) << " ";
		}
		res->clear();
		cout << endl;
	}

	return 0;
}
```
