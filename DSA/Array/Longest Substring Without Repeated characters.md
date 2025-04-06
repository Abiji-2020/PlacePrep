# Problem 
 - Need to find the longest substring without repating characters in it.
 - For example in a string `abcabc` the longest substring without repeating character is `abc` and the length is 3. We need to return the length of the longest substring without repeating characters.

## Approach 

### Brute Force

- Initially create a hashTable to store the frequency of the characters in the current string window.
- Iterate through the each character and update the frequency in the hashTable.
- If the characters are repeating, stop there and count the maxLength
- Initialize the new hashTable.

  - Time Complexity - `O(n^2)`
  
### Optimal   `(Sliding Window)`

 - Initalize the hashTable to store the lastSeenIndex
 - initalize the left parameter of the window to 0
 - Iterate through the string by expanding the right of the window by each character.
 - If the character is not seen, or already seen but not in the current window
 - Update the maxLength and update the lastSeenIndex
 - Else shrink the window by updating the left to the nextValue of the lastSeenIndex.
 - Update the lastSeenIndex.

 -   - Time Complexity -`O(n)`
  
## Code

```cpp

class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int left = 0;
        unordered_map<char, int> lastIndex;
        int maxLength = 0;
        for (int right = 0; right < s.size(); right += 1) {
            if (lastIndex.count(s[right]) == 0 || lastIndex[s[right]] < left) {
                maxLength = max(maxLength, right - left + 1);
                lastIndex[s[right]] = right;
            } else {
                left = lastIndex[s[right]] + 1;
                lastIndex[s[right]] = right;
            }
        }
        return maxLength;
    }
};
```
  
