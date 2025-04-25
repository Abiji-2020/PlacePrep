# Problem 
To design a class such that initalizes a array of integers. 
And implement the function `sumRange( int left, int right )` . Where `left` and `right` are indexes. It returns the value of the sum of elements from the pervious initalized array of integers with `left` as the start index and `right` as the end index in which both are included. 

## Approach 

 - Prefix sum method.
 - Iterate the given array and store the current sum
 - at each `i` the sum will be stored in the variable in the class.
 - At the `sumRange` function
   -  If the left is `0` return `sum[right]` as it is the entire sum till the `i` value.
   -  If left is given then we return `sum[right] - sum [left-1]` to include the left value.
  
## Code 

```C++
class NumArray {
    vector<int> ans;

public:
    NumArray(vector<int>& nums) {
        if (nums.size() < 1)
            return;
        ans.resize(nums.size());
        ans[0] = nums[0];
        for (int i = 1; i < nums.size(); i += 1) {
            ans[i] += ans[i - 1] + nums[i];
        }
    }

    int sumRange(int left, int right) {
        if (left == 0)
            return ans[right];
        else
            return ans[right] - ans[left - 1];
    }
};

/**
 * Your NumArray object will be instantiated and called as such:
 * NumArray* obj = new NumArray(nums);
 * int param_1 = obj->sumRange(left,right);
 */
```
