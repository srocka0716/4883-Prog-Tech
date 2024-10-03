# 9 - Palindrome Number

https://leetcode.com/problems/palindrome-number/description/

Given an integer x, return true if x is a 
palindrome
, and false otherwise.

 

Example 1:

Input: x = 121
Output: true
Explanation: 121 reads as 121 from left to right and from right to left.

```
#include <iostream>
using namespace std;

class Solution {
public:
    bool isPalindrome(int x) {

        //this is a long to make the number fit when its reversing it lol
        //im sure theres a better solution
        long reversedNumber = 0;
        int original = x;

        //reverse the number
        while (x > 0) {
            //this singles out the last number 
            int lastDigit = x % 10;
            reversedNumber = reversedNumber * 10 + lastDigit;
            x /= 10;
        }

        //see if the numbers are the same
        return original == reversedNumber;
    }
};
```

