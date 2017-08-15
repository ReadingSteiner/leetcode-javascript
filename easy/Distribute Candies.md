# Distribute Candies

## Descriptions: 
Given an integer array with even length, where different numbers in this array represent different kinds of candies. Each number means one candy of the corresponding kind. You need to distribute these candies equally in number to brother and sister. Return the maximum number of kinds of candies the sister could gain.

Example 1:
``` 
Input: candies = [1,1,2,2,3,3]
Output: 3
Explanation:
There are three different kinds of candies (1, 2 and 3), and two candies for each kind.
Optimal distribution: The sister has candies [1,2,3] and the brother has candies [1,2,3], too. 
The sister has three different kinds of candies. 
```

Example 2:
``` 
Input: candies = [1,1,2,3]
Output: 2
Explanation: For example, the sister has candies [2,3] and the brother has candies [1,1]. 
The sister has two different kinds of candies, the brother has only one kind of candies. 

```

### Note:
1. The length of the given array is in range [2, 10,000], and will be even.
2. The number in given array is in range [-100,000, 100,000].



## My Solution
```
/**
 * @param {string} s
 * @return {string}
 */
 // Solution A - Time Limit Exceed
var distributeCandies = function(candies) {
    let candyTypesNum = candies.filter((v,index) => {
        return candies.indexOf(v) === index
    }).length
    let candiesTotal = candies.length
    return candyTypesNum > candiesTotal/2 ? candiesTotal/2 : candyTypesNum
}

// Solution B - Using Hash
var distributeCandies = function(candies) {
    let candyHash = {}
    let candyTypesNum = 0
    for(let i = 0;i < candies.length;i ++){
        if(!candyHash[candies[i]]){
            candyHash[candies[i]] = 1
            candyTypesNum += 1;
        }
    }
    let candiesTotal = candies.length
    
    return candyTypesNum > candiesTotal/2 ? candiesTotal/2 : candyTypesNum
};
```

## Best Solution🎆
```javascript
var distributeCandies = function(candies) {
    let candy_set = new Set();
    for (let i = 0; i < candies.length; i++) {
        candy_set.add(candies[i]);
    }
    if(candy_set.size <= candies.length / 2){
        return candy_set.size;
    } else{
        return candies.length/2;
    }
};
```

## Comments
- The main idea is `Min(candyTypes, length/2)`.
- My solution A using Array's `indexOf`, which turns the time complexity from `O(n)` to `O(n^2)`, it looks really pretty on code, but wasting time for a algorithms.
- My solution B using Javascript Object as HashSet, to do the array deduplication.This time the time complexity down to `O(n)`, and it is accepeted.
- The best solution uses ES2015 `Set`, the idea is same as my solution B, but it is 2 times faster, I think maybe `Set` is actually run in C++, so it's quicker than javascript Object.






