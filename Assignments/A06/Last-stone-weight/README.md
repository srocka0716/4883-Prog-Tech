# 1046 - Last Stone Weight

https://leetcode.com/problems/last-stone-weight/description/

You are given an array of integers stones where stones[i] is the weight of the ith stone.

We are playing a game with the stones. On each turn, we choose the heaviest two stones and smash them together. Suppose the heaviest two stones have weights x and y with x <= y. The result of this smash is:

If x == y, both stones are destroyed, and
If x != y, the stone of weight x is destroyed, and the stone of weight y has new weight y - x.
At the end of the game, there is at most one stone left.

Return the weight of the last remaining stone. If there are no stones left, return 0.

 

Example 1:

Input: stones = [2,7,4,1,8,1]
Output: 1
Explanation: 
We combine 7 and 8 to get 1 so the array converts to [2,4,1,1,1] then,
we combine 2 and 4 to get 2 so the array converts to [2,1,1,1] then,
we combine 2 and 1 to get 1 so the array converts to [1,1,1] then,
we combine 1 and 1 to get 0 so the array converts to [1] then that's the value of the last stone.

```
#include <vector>
#include <queue>

using namespace std;

class Solution {
public:
    int lastStoneWeight(std::vector<int>& stones) {
        //using maxheap orders the stones from big to small
        priority_queue<int> maxHeap(stones.begin(), stones.end());

        // Continue smashing until at most one stone is left
        while (maxHeap.size() > 1) {
            //most heavy stone
            int stone1 = maxHeap.top(); 
            maxHeap.pop();
            //second heaviest stone
            int stone2 = maxHeap.top();
            maxHeap.pop();
            
            if (stone1 != stone2) {
                //if theyre not the same weight the difference is 'smashed'
                maxHeap.push(stone1 - stone2);
            }
        }

        //if theres no more stones, return 0, if theres still stones
        //return the last remaining stone
        if (maxHeap.empty()) {
            return 0;
        } else {
            return maxHeap.top();
        }
    }
};
```
