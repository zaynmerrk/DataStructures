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

#define hell    INT_MIN
template<typename T>
class QueueUsingArray {
    T *data;
    int frontIndex;
    int nextIndex;
    int size;
    int capacity;

public:
    QueueUsingArray(int s) {
        data = new T[s];
        frontIndex = -1;
        nextIndex = 0;
        size = 0;
        capacity = s;
    }

    int getSize() {
        return size;
    }

    bool isEmpty() {
        return size == 0;
    }

    void enqueue(T element) {
        if (size == capacity) {
            cout << "Queue is full" << " ";
            return;
 /*$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$*/ embed this only if you want dynamic queue	    
            T *new_data = new T[2 * capacity];
            int start = 0;
            for (int i = frontIndex; i < capacity; i++) {
                new_data[start++] = data[i];
            }
            for (int i = 0; i < frontIndex; i++) {
                new_data[start++] = data[i];
            }
            delete[] data;
            data = new_data;
	    nextIndex = capacity;
            capacity = 2 * capacity;
            frontIndex = 0;
/*$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$*/
        }

        data[nextIndex] = element;
        nextIndex = (nextIndex + 1) % capacity;
        if (frontIndex == -1) {
            frontIndex = 0;
        }
        size++;
    }

    T front() {
        if (isEmpty())
            return hell;

        return data[frontIndex];
    }

    T dequeue() {
        if (isEmpty())
            return hell;

        T ans = data[frontIndex];
        frontIndex = (frontIndex + 1) % capacity;
        size--;

        if (size == 0) {
            frontIndex = -1;
            nextIndex = 0;
        }

        return ans;
    }

};

/*^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^*/

int main() {
	/*||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||*/
#ifndef ONLINE_JUDGE
	freopen("input.txt", "r", stdin);
	freopen("output.txt", "w", stdout);
#endif
	/*||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||*/

	QueueUsingArray<int> q(6);

	q.enqueue(10);
	q.enqueue(20);
	q.enqueue(30);
	q.enqueue(40);
	q.enqueue(50);
	q.enqueue(60);


	cout << q.front() << endl;
	cout << q.dequeue() << endl;
	cout << q.dequeue() << endl;
	cout << q.dequeue() << endl;

	cout << q.getSize() << endl;
	cout << q.isEmpty() << endl;




	/*||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||*/
	return 0;
}
