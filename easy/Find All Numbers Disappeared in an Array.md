# Find All Numbers Disappeared in an Array

## Descriptions: 
Given an array of integers where 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.
Find all the elements of [1, n] inclusive that do not appear in this array.
Could you do it without extra space and in O(n) runtime? You may assume the returned list does not count as extra space.

#### Example
```
Input:
[4,3,2,7,8,2,3,1]

Output:
[5,6]
```

## My Solution
```
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var findDisappearedNumbers = function(nums) {
    let rst = []
    nums.forEach(v => {
        rst.push(0)
    })
    nums.forEach((v) => {
        rst[v-1] = 1
    })

    return rst.map((v,index) => {
        return v === 0 ? index+1 : 0
    }).filter(v => v)
};
```

## Best Solution🎆
```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var findDisappearedNumbers = function(nums) {
    let rst = []
    let n = nums.length
    for(let i = 0; i < n; i++) {
        nums[(nums[i]-1) % n] += n
    }
    for(let i = 0;i <= n; i++) {
        if(nums[i] <= n) rst.push(i+1)
    }
    return rst
};
```

## Comments
- My solution is terrible, it searchs the array 4 times.
- The best solution is really great.
	- Firstly, search the array, and increase the nums[num[i] - 1] with n. In case of multiple increase, it will % n at each time.
	- Secondly, we check the nums, those numbers which is bigger than n, means they are already appeard in the array.So we just need to filt those numbers which is less than n.





