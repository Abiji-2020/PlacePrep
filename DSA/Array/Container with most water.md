# Problem.

Given a array of heights where each `height [i]` represents the height of the line. We need to find the maximum capacity of the water that can be stored in the area, where each `i` is at a distance of 1 each. Return the maximum capacity. 

## Approach

- **Two pointer**

- Initialize start =0 and end = the last value of the heights.
- while start is less than or equal to the end we check for the maximum water capacity.
- in each iteration we take the minimum value of the two start and the end and with that and the distance between them we compute the capacity.
- compare the capacity with the previous one and update if the new one is maximum.
- We move forward the iterator start or end based on which is minimum to optimize `(Greedy Part)`.
- Time complexity - `O(n)`

## Code

```c++
class Solution {
public:
    int maxArea(vector<int>& height) {
        int start = 0, end = height.size() - 1;
        int maxContainer = 0;
        while (start <= end) {
            int minValue = min(height[start], height[end]);
            maxContainer = max(maxContainer, minValue * (end - start));
            if (minValue == height[start])
                start += 1;
            else
                end -= 1;
        }
        return maxContainer;
    }
};
```
