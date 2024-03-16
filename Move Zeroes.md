# LeetCode Problem Writeup
## Problem Title: [Move Zeroes](https://leetcode.com/problems/move-zeroes/description)

### Problem Description:

Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.
Note that you must do this in-place without making a copy of the array.

### Approach:
1. **Initialization**:
   - Initialize `zeroIndex` to 0. This variable keeps track of the position where the next non-zero element should be placed.

2. **Iteration through the Array**:
   - Iterate through the input array.
   - For each non-zero element encountered:
     - Move it to the position indicated by `zeroIndex`.
     - Increment `zeroIndex`.

3. **Filling Remaining Positions with Zeroes**:
   - After processing all non-zero elements, fill the remaining positions from `zeroIndex` to the end of the array with zeros.
  
## Code Implementation:

```java
class Solution {
    public void moveZeroes(int[] nums) {
       
      int zeroIndex = 0;
      
        for (int i = 0; i < nums.length; i++) {
           
            if (nums[i] != 0) {
                nums[zeroIndex++] = nums[i];
            }
        }
     
        while (zeroIndex < nums.length) {
            nums[zeroIndex++] = 0;
        }
    }
}
```

## Complexity Analysis:

![image](https://github.com/LuizaAlex/LeetCode/assets/123961367/5c0ef00b-e141-4993-96c4-2003fce77cc0)

**Time Complexity:**<br>
1.The algorithm traverses the input array once, so the time complexity is O(n), where n is the length of the input array.<br>

**Space Complexity:**<br>
The algorithm operates in-place without using any additional data structures, so the space complexity is O(1), constant space.<br>
