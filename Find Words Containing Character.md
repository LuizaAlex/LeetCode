# LeetCode Problem Writeup
## Problem Title: [ Find Words Containing Character](https://leetcode.com/problems/find-words-containing-character/description/)

### Problem Description:

You are given a 0-indexed array of strings words and a character x.
Return an array of indices representing the words that contain the character x.
Note that the returned array may be in any order.

 

### Approach:
1. **Initialization**:
   Initialize an empty list result to store the indices of words containing the character x.

2. **Iteration through the Array**:
   - Iterate through the array of words.
   - For each word encountered:
        - Check if the word contains the character x using the indexOf method.
         If the character x is found in the word, add the index of the word to the result list.
3. **Return the Result:**:
   - After processing all words, return the result list containing the indices of words containing the character x.
  
## Code Implementation:

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<Integer> findWordsContaining(String[] words, char x) {
        List<Integer> result = new ArrayList<>();
        
        for (int i = 0; i < words.length; i++) {
            if (words[i].indexOf(x) != -1) {
                result.add(i);
            }
        }

        return result;
    }
}

```

## Complexity Analysis:

![image](https://github.com/LuizaAlex/LeetCode/assets/123961367/8fc0a3c1-ed77-4356-9278-6b1b9d4bd913)


**Time Complexity:**<br>
1. The algorithm traverses the array of words once, and for each word, it performs a search operation using the indexOf method, which has a time complexity of O(m), 
where m is the length of the word. Therefore, the overall time complexity is O(n * m), where n is the number of words and m is the average length of the words.<br>

**Space Complexity:**<br>
The algorithm uses an additional list result to store the indices of words containing the character x. 
The size of this list depends on the number of words containing the character x, but it doesn't exceed the total number of words in the input array.
Therefore, the space complexity is O(n), where n is the number of words in the input array.<br>
