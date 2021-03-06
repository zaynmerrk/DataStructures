``` cpp
A thief robbing a store can carry a maximal weight of W into his knapsack. There are N items, and i-th item weigh 'Wi' and the value being 'Vi.'
What would be the maximum value V, that the thief can steal?
Input Format :
The first line of the input contains an integer value N, which denotes the total number of items.

The second line of input contains the N number of weights separated by a single space.

The third line of input contains the N number of values separated by a single space.

The fourth line of the input contains an integer value W, which denotes the maximum weight the thief can steal.
Output Format :
Print the maximum value of V that the thief can steal.
Constraints :
1 <= N <= 20
1<= Wi <= 100
1 <= Vi <= 100

Time Limit: 1 sec
Sample Input 1 :
4
1 2 4 5
5 4 8 6
5
Sample Output 1 :
13
Sample Input 2 :
5
12 7 11 8 9
24 13 23 15 16
26
Sample Output 2 :
51


/*^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^*/  //exponenational
#include <iostream>
using namespace std;
int knapsack(int* wt, int* val, int n, int maxWeight){
   if(!n || !maxWeight)
   	return 0;
    
   //if you miss this step then algo will get prune
  // because we are returning maximum(greedy) so it become more of greedy choice
   if(wt[0]>maxWeight) //discard as it cant gets fit in knapsack
   	return knapsack(wt+1,val+1,n-1,maxWeight);
	
	
   int includeWt = val[0] + knapsack(wt+1,val+1,n-1,maxWeight-wt[0]);
   
   // OR YOU THIS IF YOU DONT WANT IF CONDITION STATEMENT
  //  int includeWt = (wt[0]>maxWeight) ? INT_MIN : val[0] + knapsack(wt+1,val+1,n-1,maxWeight-wt[0]);
  
   int excludeWt = knapsack(wt+1,val+1,n-1,maxWeight);

   return max(includeWt,excludeWt);
}
                                                     ON 2D GRID ---------------------------- SPACE (N*W)
/*^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^*/  //memoization
#include <iostream>
using namespace std;
int knapsack(int* wt, int* val, int n, int maxWeight, int **dp) {
	if (!n || !maxWeight)
		return 0;

	if (dp[n - 1][maxWeight - 1] != -1)
		return dp[n - 1][maxWeight - 1];

	int includeWt = (wt[0] > maxWeight) ? INT_MIN : val[0] + knapsack(wt + 1, val + 1, n - 1, maxWeight - wt[0], dp);
	int excludeWt = knapsack(wt + 1, val + 1, n - 1, maxWeight, dp);

	dp[n - 1][maxWeight - 1] = max(includeWt, excludeWt);

	return dp[n - 1][maxWeight - 1];
}


int knapsack(int* wt, int* val, int n, int maxWeight) {
	int **dp = new int*[n + 1];

	for (int i = 0; i <= n; i++) {
		dp[i] = new int[maxWeight + 1];
		for (int j = 0; j <= maxWeight; j++) {
			dp[i][j] = -1;
		}
	}

	return knapsack(wt, val, n, maxWeight, dp);
}

```

