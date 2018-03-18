# 7. Reverse Integer

## Link

https://leetcode.com/problems/reverse-integer/description/

## Question

Given a 32-bit signed integer, reverse digits of an integer.
Return 0 when overflows.

**Example:**

```
123 = 321
-123 = -321
1230 = 321
```

## Solution - Reversed String

Convert integer to string, than reverse the string, finally convert the string back to integer.
Following are some corner cases need to be considered.

**(1) Number ends with zeros**

Keep divide the number by 10 when its modulus with 10 is zero. 
But need aware that 0 might result an infinite loop.

**(2) Negative Integer**

Reverse the string directly will result an invalid integer, like `-123=321-`.
Therefore remove negative sign first than convert it to string, and add it back after the number is reversed.

**(2) Integer Overflows**

This case happens when integer starts with smaller digit, but ends with greater one.
In java, `Integer.valueOf` will throw `NumberFormatException` when interger overflows, 
therefor we can catch the exception and return 0 when integer overflows.

```
1534236469 = 9646324351 (Overflows)
```

### Solution (Java)

```java
class Solution {
    public int reverse(int x) {
        if (x == 0) {
            return 0;
        }
        
        while (x % 10 == 0) {
            x = x / 10;
        }
        
        boolean isNegative = x < 0;
        if (isNegative) {
            x = -x;
        }
        
        String str = String.valueOf(x);
        str = new StringBuilder(str).reverse().toString();
        
        try {
            Integer result = Integer.valueOf(str);
            return isNegative ? -result : result;
        } catch (Exception e) {
            return 0;
        }        
    }
}
```






