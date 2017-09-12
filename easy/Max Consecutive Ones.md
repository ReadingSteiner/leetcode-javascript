# Max Consecutive Ones

## Descriptions: 
Given a binary array, find the maximum number of consecutive 1s in this array.

#### Example 1
```
Input: [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3.
```

#### note:
1. The input array will only contain `0` and `1`.
2. The length of input array is a positive integer and will not exceed 10,000

## My Solution
```
// Solution A
var findMaxConsecutiveOnes = function(nums) {
    let max = 0
    let tempMax = 0
    for(let i = 0; i < nums.length; i++) {
        if(nums[i] === 1) {
            tempMax++
        }else{
            if(tempMax > max)
                max = tempMax
            tempMax = 0
        }
    }
    if(tempMax > max) max = tempMax
    return max
};

//Solution B  one liner
var findMaxConsecutiveOnes = function(nums) {
    return Math.max.apply(null, nums.join('').split('0').map(v => v.length))
};
```

## Best Solution🎆
```javascript
    let count = 0, max = 0;
    for (let num of nums) {
        if (num === 1) count++;
        else count = 0;
        max = Math.max(count, max);
    }
    return max;
```

## Comments
- My solution A is follwing my instinct, little bit verbose.
- My solution B is a one-liner, using Function.prototype.apply and Math.max to get the max length of 1s group, but this solution is time wasting.
- Best solution is still the same idea with A, but it is more concise.





