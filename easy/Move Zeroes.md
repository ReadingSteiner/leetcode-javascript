# Move zeros

## Descriptions: 
Given an array `nums`, write a function to move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.
For example, given `nums = [0, 1, 0, 3, 12]`, after calling your function, `nums` should be `[1, 3, 12, 0, 0]`.



#### Note
1. You must do this **in-place** without making a copy of the array.
2. Minimize the total number of operations.

## My Solution
```
I only came out the native way.
```

## Best Solution🎆
```javascript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    for(let zeroPosition = 0,i = 0; i < nums.length; i++ ){
        if(nums[i] != 0){
            let temp = nums[i]
            nums[i] = nums[zeroPosition]
            nums[zeroPosition++] = temp
        }
    }
};
```

## Comments
- Say we have two pointer, one is the current, and the another is the position of the last zero.
- Then we scan the array one by one, once we find a non-zero element, we swap it with the last zero.
- When there is no zero at start, we are just swapping elements themselves.
- When there are one or more zeros, we are swapping the first zero with following non-zero elments.
- Finally, we have all zeros at the end of array.






