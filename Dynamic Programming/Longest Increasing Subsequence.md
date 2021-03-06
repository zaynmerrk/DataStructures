``` cpp
Given an array with N elements, you need to find the length of the longest subsequence in the given array such that all elements of the subsequence are sorted in strictly increasing order.
Input Format
The first line of input contains an integer N. The following line contains N space separated integers, that denote the value of elements of array.
Output Format
The first and only line of output contains the length of longest subsequence.
Constraints
1 <= N <= 10^3
Time Limit: 1 second

/*^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^*/ //exponenational
int longestIncreasingSubsequence(int *nums, int n, int prev) {
	if (!n)
		return 0;

	int taken;
	if (nums[0] > prev) {
		taken = longestIncreasingSubsequence(nums + 1, n - 1, nums[0]) + 1;
	}

	int notTaken = longestIncreasingSubsequence(nums + 1, n - 1, nums[0]);


	return max(taken, notTaken);
}
int longestIncreasingSubsequence(int *nums, int n) {

	return longestIncreasingSubsequence(nums, n, 0);
}

/*^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^*/  //dynamic prog..
int longestIncreasingSubsequence(int arr[], int n) {
	if (!n)
		return 0;
	
	int *dp = new int[n];

	for (int i = 0; i < n; i++) {
		dp[i] = 1;
		for (int j = 0; j < i; j++) {
			if (arr[j] < arr[i]) {
				dp[i] = max(dp[j] + 1, dp[i]);
			}
		}
	}

	int best = -1;
	for (auto it=0;it<n;it++) {
		best = max(best, dp[it]);
	}

	delete []dp;
	return best;
}

/*^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^*/  // more optimised O(nlogn) time complex //dp + binary search(patience sort)

// refrence --  https://leetcode.com/problems/longest-increasing-subsequence/discuss/74848/9-lines-C%2B%2B-code-with-O(NlogN)-complexity




int longestIncreasingSubsequence(int arr[], int n) {
	if (!n)
		return 0;

	vector<int> res;

	for (int i = 0; i < n; i++) {
		auto it = std::lower_bound(res.begin(), res.end(), arr[i]);
		if (it == res.end())
			res.push_back(arr[i]);
		else
			*it = arr[i];
	}

	return res.size();
}
```
