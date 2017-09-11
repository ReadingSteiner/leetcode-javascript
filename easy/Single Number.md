# Single Number

## Descriptions: 
Given an array of integers, every element appears twice except for one. Find that single one.


#### note:
1. Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

## My Solution
```
var singleNumber = function(nums) {
    let showMap = {}
    
    for(let i = 0; i < nums.length; i++) {
        if(showMap[nums[i]] === undefined) {
            showMap[nums[i]] = 0
        }else{
            showMap[nums[i]] ++
        }
    }
    for(key in showMap){
        if(showMap[key] === 0)
            return Number(key)
    }
};
```

## Best Solution🎆
```javascript
var singleNumber = function(nums) {
    return nums.reduce((acc, num) => num ^ acc, 0);
};
```

## Comments
- My solution is follwing instinct.
- The best solution is very smart, since every number XOR itself will be 0, and any non-zero number XOR 0 will be the number itself.Because there is only one single number so the continuously XOR operating result will eventually be the single number.





