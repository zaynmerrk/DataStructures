``` cpp
/*++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*/-------------------------------------SAME QUESTION
```
https://leetcode.com/problems/remove-duplicate-letters/

``` cpp
/*++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*/----------------------------------------------------SAME QUESTION
```
https://leetcode.com/problems/smallest-subsequence-of-distinct-characters/ 
``` cpp
/*++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*/----------------------------------------------------------------------MY SOLUTION
```
https://leetcode.com/problems/remove-duplicate-letters/discuss/906973/C%2B%2B-Simple-with-comments-0-ms-faster-than-100.00-easy-buzzy

``` cpp
/*++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*/
class Solution {
public:
    string removeDuplicateLetters(string s) {
        int *count = new int[26];
        bool *taken = new bool[26];

        for (int i = 0; i < 26; i++){
            count[i] = 0;
            taken[i] = 0;      //false
        }

        for (auto it : s) {
            int ch = it - 97;
            count[ch]++;
        }
         string result = "";
        for (auto it : s) {
            int ch = it - 97;
            count[ch]--;

            if (taken[ch])       // already present in result
                continue;

            while (!result.empty() && it < result.back() && count[result.back()-97]) {
                taken[result.back()-97] = false;    //now not in result
                result.pop_back();
            }
            result += it;
            taken[ch] = true;    // here taking into result
        }

        return result;
    }
};
