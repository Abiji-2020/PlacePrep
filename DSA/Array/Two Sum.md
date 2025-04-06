# Problem

- Given a array of integers and a target. We need to find two values which will add up to the target  value.
- Given in such a way that their is only unique solution exists.

## Constraints

- 2 <= nums.length <= 10^4
- 10^9 <= nums[i] <= 10^9
- 10^9 <= target <= 10^9
- Only one valid answer exists.

## Approach
  - Iterate the given array.
  - Check for the complement value present in the hashtable.
  - If the complement value is present return the current index and complement index. 
  - Else in a hashtable add a entry  with  complement values (`target - nums[i]`) as key and `index` as value.

  ## Code

  ```c++
  class Solution {
  public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> hashTable;
        for (int i = 0; i < nums.size(); ++i) {
            int complement = target - nums[i];
            if (hashTable.find(complement) != hashTable.end()) {
                return {i, hashTable[complement]};
            }
            hashTable[nums[i]] = i;
        }
        return {-1, -1}; // Not found
    }
};

  ```
