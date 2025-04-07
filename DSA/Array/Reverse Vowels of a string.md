# Problem 
- Given a string we need to select only the vowel characters and reverse them. 
- For example if a string is `"IceCream"` then it should be converted into `"aceCreIm"`.

## Approach 

### Brute Force `2 Pass`

 - Initalize  a helper function which computes whether the given character is vowel or not.
 - Iterate through the list from left to right and store the vowels in a new string in the same order.
 - Iterate through the list from right to left and in this pass update at the indexes where the vowel is occured.

### Optimal `Single Pass`

- Initalize a helper function which checks whether the given character is vowel or not.
- Have two pointers `left` and `right` where left is the beginning of the string and the right is the end of the string.
- Iterate till the left pointer is greater than the right pointer
  - Iterate t left pointer points  vowel character.
  - Iterate right pointer until it shows the vowel character.
  - swap the characters.
    
**`Time Complexity: O(n)`**

### Code 

```c++
class Solution {
public:
    string reverseVowels(string s) {
        int left = 0;
        int right = s.size() - 1;
        auto isVowel = [](const char c) {
            string vowel = "aeiouAEIOU";
            return vowel.find(c) < 10;
        };

        while (left <= right) {
            while (left < s.size() && !isVowel(s[left]))
                left += 1;
            while (right >= 0 && !isVowel(s[right]))
                right -= 1;
            if (left <= right && left < s.size() && right >= 0)
                swap(s[left], s[right]);
            left += 1;
            right -= 1;
        }
        return s;
    }
};
```
