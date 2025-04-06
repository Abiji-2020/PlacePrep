# Problem 
Given a unsorted array of integers need to find the longest consecutive sequence of numbers `( a numbers which differ by only value 1 )`. And the expected time constraint to do this is `O(n)`.

## Constraints

- length of array will be of `10^5`.
- each value will range from `-10^9` to `10^9`.

## Approach

 - Create a new unordered_set (`O(1)` lookup) with the given values from the integers.
 - Iterate over the set and check if the previous element exists on the set.
 - If previous element exists skip and iterate over the element.
 - If no previous element exists then from that iterate by checking add a 1 and increase the count until there are no element is there in the set.

## Code

```c++
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        unordered_set<int> s(nums.begin(),nums.end());
        int longest = 0;
        for(int val: s){
            if(s.find(val-1) == s.end()){
                int curr =0;
                int cv = val;
                while(s.find(cv)!=s.end()){
                    curr+=1;
                    cv+=1;
                }
                longest = max(longest, curr);
            }
        }
        return longest;
    }
};
```
---

