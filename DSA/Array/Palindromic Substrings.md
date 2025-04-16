# Problem : 

To return the number of palindromic substrings in the given string. 

## Approach 

- **Expand Around the centre method**
- Initialy create a helper function which expands the string.
- The function should take the left and right position of the string
- Count the number of palindromes and return it.
- by expanding on the both sides it cheks for the left is equal to right
- Then iterate the string by each character and expand it as center
- expand for both the odd and even palindrome.
- add all of them to the total-count.

- Time complexity - `O(n^2)`

### Code 

```c++
class Solution {
public:
    int countSubstrings(string s) {
        int count = 0;
        auto expand = [&](int i, int j) {
            int left = i, right = j;
            int curr_count = 0;
            while (left >= 0 && right < s.size() && s[left] == s[right]) {
                curr_count += 1;
                left -= 1;
                right += 1;
            }
            return curr_count;
        };
        for (int i = 0; i < s.size(); i += 1) {
            int evenPali = expand(i, i);
            int oddPali = expand(i, i + 1);
            count += evenPali + oddPali;
        }
        return count;
    }
};
```
