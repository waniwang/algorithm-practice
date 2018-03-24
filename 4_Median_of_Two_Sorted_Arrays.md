# 4. Median of Two Sorted Arrays

## Link

https://leetcode.com/problems/median-of-two-sorted-arrays/description/

## Qeustion

There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

## Solution - Naive Sort

Combine two arrays and use build-in sort function.

**Ruby Code**

```
def find_median_sorted_arrays(nums1, nums2) 
   nums = (nums1 + nums2).sort 
   size = nums.size
   if size == 0
       return 0
   end
   if size == 1
       return nums[0]
   end
    
   index = size / 2
   if size % 2 == 0
       (nums[index] + nums[index - 1]).to_f / 2
   else 
       nums[index]
   end    
end
```

**Java Code**

```
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        
        int[] nums = new int[nums1.length + nums2.length];
        System.arraycopy(nums1, 0, nums, 0, nums1.length);
        System.arraycopy(nums2, 0, nums, nums1.length, nums2.length);

        if (nums.length == 0) {
            return 0;
        }
        if (nums.length == 1) {
            return nums[0];
        }
        
        Arrays.sort(nums);
        
        int index = nums.length / 2;
        
        if (nums.length % 2 == 0) {
            return Double.valueOf(nums[index] + nums[index - 1]) / 2;
        } else {
            return nums[index];
        }
    }
}
```