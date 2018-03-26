# 1. Two Sum

## Link

https://leetcode.com/problems/two-sum/description/

## Question

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

## Solution

Key idea is to utilize map to accelerate.
The key of the map will be the number we traversed, and the value will be the index.
When traversing numbers, check if there's any key equals `target - current_number`, so that `(target - current_number) + current_number` will equals to target. If no match found, put the current number into the map.

**Java code**

```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        if (nums.length < 2) {
            return null;
        }
        
        HashMap map = new HashMap<Integer, Integer>();

        for (int i = 0; i < nums.length; i++) {
            int number = nums[i];
            Integer targetKey = Integer.valueOf(target - number);
            if (map.containsKey(targetKey)) {
                return new int[]{ (int) map.get(targetKey), i};
            } else {
                map.put(number, i);
            }
        }
        
        return null;
    }
}
```