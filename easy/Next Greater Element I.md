# Next Greater Element I

## Descriptions: 
You are given two arrays (without duplicates) nums1 and nums2 where nums1’s elements are subset of nums2. Find all the next greater numbers for nums1's elements in the corresponding places of nums2.
The Next Greater Number of a number x in nums1 is the first greater number to its right in nums2. If it does not exist, output -1 for this number.



#### Example 1:
``` 
Input: nums1 = [4,1,2], nums2 = [1,3,4,2].
Output: [-1,3,-1]
Explanation:
    For number 4 in the first array, you cannot find the next greater number for it in the second array, so output -1.
    For number 1 in the first array, the next greater number for it in the second array is 3.
    For number 2 in the first array, there is no next greater number for it in the second array, so output -1.
```

#### Example 2:
```
Input: nums1 = [2,4], nums2 = [1,2,3,4].
Output: [3,-1]
Explanation:
    For number 2 in the first array, the next greater number for it in the second array is 3.
    For number 4 in the first array, there is no next greater number for it in the second array, so output -1.
```

#### note:
1. All elements in `nums1` and `nums2` are unique.
2. The length of both `nums1` and `nums2` would not exceed 1000.



## My Solution
```
var nextGreaterElement = function(findNums, nums) {
    let biggerMap = {}
    for(let i = 0; i < nums.length -1; i++) {
        for(let j = i+1; j < nums.length; j++) {
            if(nums[i] < nums[j]){
                biggerMap[nums[i]] = nums[j]
                break
            }
        }
    }
    
    return findNums.map(v => {
        return biggerMap[v] ? biggerMap[v] : -1
    })
};
```

## Best Solution🎆
```javascript
var nextGreaterElement = function(findNums, nums) {
    let biggerMap = {}
    let stack = []
    for(let i = 0; i < nums.length; i++) {
        while(stack.length && stack[stack.length-1] < nums[i]){
            biggerMap[stack.pop()] = nums[i]
        }
        stack.push(nums[i])
    }
    
    return findNums.map(v => {
        return biggerMap[v] ? biggerMap[v] : -1
    })
};
```

## Comments
- My idea of using `Map` is good.
- However my solution has `O(n^2)` time complexity.
- The best solution using stack, little bit hard for me to understand.
	- 	the loop still start from left to right
	-  stack push every element at each loop, but it is keeping decreasing stack.
	-  In order to maintain the "decreasing", once it meet a "bigger" element, it will take all the elements less than it out.
	-  and becuz of the "decreasing" stack, it is exactly the next greater element of all elements it takes out.
 





