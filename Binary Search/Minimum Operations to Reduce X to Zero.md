``` cpp
// https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/

class Solution {
public:
	int minOperations(vector<int>& nums, int x) {
		int target = -x;
		for (auto it : nums)
			target += it;

		if (target == 0)
			return nums.size();

		unordered_map<int, int>map;
                 map[0]=-1;
        
		int res = -1;
		int sum = 0;

		for (int i = 0; i<nums.size(); i++) {

			sum += nums[i];

			if (map.find(sum - target) != map.end()) {
				res = max(res, i - map[sum - target]);
			}

			map[sum] = i;
		}
		return res != -1 ? nums.size() - res : res;
	}
}; 
```