# 191 - Number of 1 Bits

https://leetcode.com/problems/number-of-1-bits/

Write a function that takes the binary representation of a positive integer and returns the number of 
set bits
 it has (also known as the Hamming weight).

 

Example 1:

Input: n = 11

Output: 3

Explanation:

The input binary string 1011 has a total of three set bits.

```
class Solution {
public:
    vector<int> decimalToBinary(int n) {
        vector<int> binaryNum;

        
        while (n > 0) {
            binaryNum.push_back(n % 2); 
            n = n / 2;                  
        }

        return binaryNum;
    }
    int hammingWeight(int n) {
        int count = 0;

        while (n > 0) {
            if (n % 2 == 1)
                count++;
            n = n / 2;
        }

        return count;
    }
};
```
