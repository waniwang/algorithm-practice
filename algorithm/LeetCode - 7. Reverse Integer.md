# 7. Reverse Integer

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

### Idea

Convert integer to string, than reverse the string, finally convert the string back to integer.

### Corner cases

#### (1) Number ends with zeros

**Example**

```
1230000 = 321
```

**Solution**

Keep divide the number by 10 when its modulus with 10 is zero. But here need to be aware of that 0 might result an infinite loop.

#### (2) Minus Value

**Example**

```
-123 = -321
```

**Solution**

If just feed the integer to string direclty and reverse will create an number with invalid format, like `-123=321-`.
Therefore we convert the negative value to positive first, then convert it back to negative after the number is reversed.

#### (2) Integer Overflows

**Example**

```
1534236469 = 9646324351 (Overflows)
```

**Soltion** 

This case happens when input starts with smaller digit, but its detail is greater than it.
In java, when convert a string to integer by using Integer.valueOf(input), will raise NumberFormatException when integer overflows. Thus we can catch this exception and return 0 when catch this exception.

### Solution in Java

```
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







