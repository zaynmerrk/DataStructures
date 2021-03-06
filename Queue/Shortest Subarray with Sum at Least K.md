https://leetcode.com/problems/shortest-subarray-with-sum-at-least-k/

/*^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^*/  

https://leetcode.com/problems/shortest-subarray-with-sum-at-least-k/discuss/549959/Video-Solution-and-Java-Deque-Code


/*^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^*/
``` cpp

class Solution {
public:
    int shortestSubarray(vector<int>& nums, int K) {
        int n = nums.size();

        if (!n)
            return -1;

        int result = INT_MAX;
        deque<int> dq;

        for (int i = 0; i < n; i++) {
            if (i > 0) {
                nums[i] += nums[i - 1];
            }

            if (nums[i] >= K) {
                result = min(result, i + 1);
            }

            while (!dq.empty() && nums[i] - nums[dq.front()] >= K) {
                result = min(result, i - dq.front());
                dq.pop_front();
            }
           
           /*

For example, here give a A[5] = A[84, -37, 32, 40, 95]. Then the accumulate array B will be B[6] = [0, 84, 47, 79, 119 ,214]. Give the K = 125. And we store the answer length at res.
Now we focus at two case, B[5] - B[1] and B[5] - B[2]. Both of those are fit condition that >= K.
Below follow :
B[5] - B[1] = 130. And because 130 >= K, we store the length for 1 to 5, make res = 5.
B[5] - B[2] = 167, And because 167 >= K, we store the length for 2 to 5, make res = 4.
From those two case, you can notice that actually we do not need to calculate case B[5] - B[1].
The reason is B[2] < B[1]. So if B[5] - B[1] fit the condition(B[5] - B[1] >= K), then B[5] - B[2] will must fit the condition. And B[5] - B[2] will have short length than B[5] - B[1].
This is why we do "while d and B[i] <= B[d[-1]]: d.pop()".

I try my best to explain my thought in english.
If you still feel confuse, please let me know.

           */

            while (!dq.empty() && nums[i] <= nums[dq.back()]) {
                dq.pop_back();
            }

            dq.push_back(i);
        }

        if (result == INT_MAX)
            return -1;
        return reuslt;
    }
};
