# 7 - Reverse Integer

https://leetcode.com/problems/reverse-integer/description/

Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

 

Example 1:

Input: x = 123
Output: 321
Example 2:

Input: x = -123
Output: -321
Example 3:

Input: x = 120
Output: 21

```
#include <iostream>
#include <limits.h>  // For INT_MAX and INT_MIN

class Solution {
public:
    int reverse(int x) {
    int reversed = 0;
    //while number isnt empty
    while (x != 0) {
        //same as the palindrome problem honestly
        //just singling out the last digit
        int lastDigit = x % 10;
        x /= 10;         
        
       //making sure that the number does go above or below limits
       //cant lie chatgpt helped me make this logic
        if (reversed > INT_MAX / 10 || (reversed == INT_MAX / 10 && lastDigit > 7)) 
        {
            return 0; 
        }
        if (reversed < INT_MIN / 10 || (reversed == INT_MIN / 10 && lastDigit < -8))
        {
            return 0; 
        }
        
        //again same as palindrome
        reversed = reversed * 10 + lastDigit;
    }
    
    return reversed;
}
};
```
