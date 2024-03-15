# LeetCode Problem Writeup
## Problem Title: [String Compression](https://leetcode.com/problems/string-compression/description/?envType=study-plan-v2&envId=leetcode-75)

### Problem Description:
Given an array of characters chars, compress it using the following algorithm:
Begin with an empty string s. For each group of consecutive repeating characters in chars:

If the group's length is 1, append the character to s.
Otherwise, append the character followed by the group's length.
The compressed string s should not be returned separately, but instead, be stored in the input character array chars. Note that group lengths that are 10 or longer will be split into multiple characters in chars.
After you are done modifying the input array, return the new length of the array.
You must write an algorithm that uses only constant extra space.


### Approach:
1. **Initialization**:
   - Initialize variables:
     - `indexCompressedArray`: Pointer to update the compressed array.
     - `count`: Count of consecutive repeating characters.
     - `prevChar`: Stores the previous character encountered.
   - Start from the second character of the input array.

2. **Iteration through the Array**:
   - Iterate through the input array starting from index 1.
   - For each character:
     - If the character is the same as the previous character (`chars[i] == prevChar`):
       - Increment the `count`.
     - If the character is different from the previous character:
       - Append the previous character to the compressed array at position `iindexCompressedArray`.
       - If `count` is greater than 1:
         - Convert `count` to a string and append each digit to the compressed array at subsequent positions.
       - Update `prevChar` with the current character, reset `count` to 1, and increment `indexCompressedArray`.

3. **Processing the Last Group of Characters**:
   - After the loop ends, handle the last group of characters in a similar manner as above.

4. **Return the New Length**:
   - Return `indexCompressedArray`, which represents the new length of the compressed array.

## Code Implementation:

```java
class Solution {
    public int compress(char[] chars) {
          int indexCompressedArray = 0;
        int count = 1; // count of consecutive repeating characters
        char prevChar = chars[0];

        for(int i =1; i< chars.length; i++){
            if(chars[i] == prevChar) {
                count++; // increment count for consecutive repeating characters
            }
            else{
                chars[indexCompressedArray++] = prevChar;
                // If count is greater than 1, append count as a separate character(s)
                if (count > 1) {
                    String countStr = String.valueOf(count);
                    for (char c : countStr.toCharArray()) {
                        chars[indexCompressedArray++] = c;
                    }
                }

                prevChar = chars[i]; // Update previous character
                count = 1; // Reset count for the new character
            }
        }

        // Process the last group of characters
        chars[indexCompressedArray++] = prevChar;
        if (count > 1) {
            String countStr = String.valueOf(count);
            for (char c : countStr.toCharArray()) {
                chars[indexCompressedArray++] = c;
            }
        }

      return indexCompressedArray;
        
    }
}
```

## Complexity Analysis:

![image](https://github.com/LuizaAlex/LeetCode/assets/123961367/45db9835-52da-4a7b-bb4d-6f536495ad78)

**Time Complexity:**<br>
1.The algorithm traverses the input array of characters once in a single pass.<br>
2. As each character is processed only once, the time complexity is linear, O(n), where n is the length of the input array.<br>


**Space Complexity:**<br>
1.The algorithm uses only a constant amount of extra space regardless of the size of the input array.<br>
2. The space complexity is O(1), as it does not depend on the size of the input.<br>
