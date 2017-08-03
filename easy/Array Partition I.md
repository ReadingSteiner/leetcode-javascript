# Array Partition I

## Descriptions: 
Given an array of 2n integers, your task is to group these integers into n pairs of integer, say (a1, b1), (a2, b2), ..., (an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible.

Input:
``` 
Input: [1,4,3,2]

Output: 4
Explanation: n is 2, and the maximum sum of pairs is 4 = min(1, 2) + min(3, 4).
```

**Note:** 
1.	n is a positive integer, which is in the range of [1, 10000].
2.	All the integers in the array will be in the range of [-10000, 10000].




## My Solution
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var arrayPairSum = function(nums) {
    return nums
            .sort((a,b) => {return a - b})
            .filter((v,i) => {return i % 2 === 0})
            .reduce((prev,next) => {return prev + next}, 0)
};
```

## Best Solution🎆
```javascript
var arrayPairSum = function(nums) {
    return nums
            .sort((a,b) => {return a - b})
            .reduce((prev,next,i) => {
                if(i % 2 === 0) {
                    return prev + next
                }else {
                    return prev
                }
            }, 0)
};
```

## Comments
- I think my solution looks really easy to read and understand, but it has more time complexity.
- I don't think the best solution is better, this is just a trade-off between time complexity & readability.






