# LeetCode - 14. Longest Common Prefix

## Link

[https://leetcode.com/problems/longest-common-prefix/description/
](https://leetcode.com/problems/longest-common-prefix/description/
)

## Description

Write a function to find the longest common prefix string amongst an array of strings.

(Return empty string when not found)

## Solution

Use a cursor index to compare each char in of the string in the array. If they are all the same the cursor will plus 1 and iterate the string in the array again to find the next common string. Stops when one of the char is not equal or the string length is equal or less than the cursor index.

**Java code**

```
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs.length == 0) {
            return "";
        }
        
        if (strs.length == 1) {
            return strs[0];
        }
        
        String result = "";
        int currentIndex = 0;
        boolean stop = false;
        
        while (!stop) {           
            if (currentIndex >= strs[0].length()) {
                return result;
            }
            String current = strs[0].substring(currentIndex, currentIndex + 1);

            for (int i=1; i<strs.length; i++) {
                if (currentIndex >= strs[i].length()) {
                    return result;
                }
                String target = strs[i].substring(currentIndex, currentIndex + 1);
                if (!target.equals(current)) {
                    return result;
                }
            }
            
            result += current;
            
            currentIndex++;
        }
        
        return result;
    }
}
```