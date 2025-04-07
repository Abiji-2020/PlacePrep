# Problem 

- Given a string, we need to find the longest substring which is a palindrome.

Example for a string `babab` there are two valid long substrings `aba` and `bab`. 

## Approach 

### BruteForce `O(n^3)`

- Helper functions which checks the given string is palindrome or not.
- Iterate the complete each substring from 0 to s.
- Call the helper function and note down the current longest palindrome.

### Optimized (Center expand method) `O(n^2)`

- Helper function to expand from the center (Slinding window).
  - Given two index. expand to left and right until the condition left character is not equal to the right character.
  - create a substring in the window and return it .
  - Length will be calculated using `left-right-1`.
- Iterate through the string
- For each index i, to check for the odd palindrome `expand(i,i)`
- to check for even palindrome `expand(i,i+1)`
- Save the longest string. and return it after the end of the iteration.


## Code

```C++
class Solution {

public:
    string longestPalindrome(string s) {
        auto expand = [&](int i, int j) {
            int left = i, right = j;
            while (left >= 0 && right < s.size() && s[right] == s[left]) {
                left -= 1;
                right += 1;
            }
            return s.substr(left + 1, right - left - 1);
        };
        string longest = "";
        for (int i = 0; i < s.size(); i += 1) {
            string odd = expand(i, i);
            if (odd.size() > longest.size())
                longest = odd;
            string even = expand(i, i + 1);
            if (even.size() > longest.size())
                longest = even;
        }
        return longest;
    }
};
```
