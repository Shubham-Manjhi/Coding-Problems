# Container With Most Water

## Question

You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

Notice that you may not slant the container.

## Example

### Example 1

**Input:** 

    height = [1,8,6,2,5,4,8,3,7]

**Output:** 

    49

**Explanation:**

    The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.

### Example 2

**Input:** 

    height = [1,1]

**Output:** 

    1

**Explanation:**

    The above vertical lines are represented by array [1,1]. In this case, the max area of water (blue section) the container can contain is 1.

## Solution

### Java

```java
public class Solution {
    public int maxArea(int[] height) {
        int maxarea = 0, l = 0, r = height.length - 1;
        while (l < r) {
            maxarea = Math.max(maxarea, Math.min(height[l], height[r]) * (r - l));
            if (height[l] < height[r])
                l++;
            else
                r--;
        }
        return maxarea;
    }
}
```

### Python

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        maxarea, l, r = 0, 0, len(height) - 1
        while l < r:
            maxarea = max(maxarea, min(height[l], height[r]) * (r - l))
            if height[l] < height[r]:
                l += 1
            else:
                r -= 1
        return maxarea
```

### C++

```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
        int maxarea = 0, l = 0, r = height.size() - 1;
        while (l < r) {
            maxarea = max(maxarea, min(height[l], height[r]) * (r - l));
            if (height[l] < height[r])
                l++;
            else
                r--;
        }
        return maxarea;
    }
};
```
```

Please note that the code provided in Java, Python, and C++ all follow the same logic. They use two pointers, one at the beginning of the array and one at the end. They calculate the area between these two lines and keep track of the maximum area seen so far. Then they move the pointer pointing to the shorter line towards the other end by one step. This is because if we moved the pointer at the longer line inwards, we would not gain any increase in area, since it is limited by the height of the shorter line.