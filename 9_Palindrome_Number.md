# 9. Palindrome Number

## Link

https://leetcode.com/problems/palindrome-number/description/

## Question

Determine whether an integer is a palindrome. Do this without extra space.
(False when the number is negative)

## Solution - Compare Number Digit 

**Java code**

```
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0) {
            return false;
        }
        
        if (x == 0) {
            return true;
        }
        
        int value = x;
        int powerOfTen = 0;
        while (value != 0) {
            value = value / 10;
            if (value != 0) {
                powerOfTen++;
            }
        }
        
        if (powerOfTen == 0) {
            return true;
        }
        
        int head = powerOfTen;
        int tail = 0;
        while (head >= tail) {
            int headDigit = numberAtDigit(x, head);
            int tailDigit = numberAtDigit(x, tail);
                        
            if (headDigit != tailDigit) {
                return false;
            }
            head--;
            tail++;
        }
        
        return true;
    }
    
    public int numberAtDigit(int number, int digit) {
        // Here we didn't handle the case digit larger than the number
        return (number % (int) Math.pow(10, digit + 1)) / (int) Math.pow(10, digit);
    }
        
}
```