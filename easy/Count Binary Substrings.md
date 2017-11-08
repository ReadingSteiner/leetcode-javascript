# Count Binary Substrings

## Descriptions: 
Give a string s, count the number of non-empty (contiguous) substrings that have the same number of 0's and 1's, and all the 0's and all the 1's in these substrings are grouped consecutively.
Substrings that occur multiple times are counted the number of times they occur.

#### Example1
```
Input: "00110011"
Output: 6
Explanation: There are 6 substrings that have equal number of consecutive 1's and 0's: "0011", "01", "1100", "10", "0011", and "01".

Notice that some of these substrings repeat and are counted the number of times they occur.

Also, "00110011" is not a valid substring because all the 0's (and 1's) are not grouped together.
```

#### Example2
```
Input: "10101"
Output: 4
Explanation: There are 4 substrings: "10", "01", "10", "01" that have equal number of consecutive 1's and 0's.
```

## My Solution
```
/**
 * @param {string} s
 * @return {number}
 */
var countBinarySubstrings = function(s) {
    let groups = [1]
    for(let i = 1; i < s.length; i++){
        if(s[i] !== s[i-1]){
            groups.push(1)
        }else{
            groups[groups.length-1]++
        }
    }

    return groups.reduce((prev,cur,i) => {
        let next = groups[i]
        let last = i === 0 ? 0 : groups[i-1]
        return prev + Math.min(next,last)
    },0)
};
```

## Best Solution🎆
```javascript
/**
 * @param {string} s
 * @return {number}
 */
var countBinarySubstrings = function(s) {
    if (!s || !s.length) {
        return 0;
    }
    
    let prevCount = 0;
    let currCount = 1;
    let currentChar = s.charAt(0);
    
    let res = 0;
    for (let i = 1; i < s.length; i++) {
        if (s.charAt(i) === currentChar) {
            currCount++;
            continue;
        } else {
            res += Math.min(prevCount, currCount);
            prevCount = currCount;
            currCount = 1;
            currentChar = s.charAt(i); 
        }
    }
    
    res += Math.min(prevCount, currCount);
    return res;
};
```

## Comments
Best solution is more time saving.

⤵️These comments coppied from leetcode.com - solution
### Intuition
We can convert the string `s` into an array `groups` that represents the length of same-character contiguous blocks within the string. For example, if s = `"110001111000000"`, then `groups = [2, 3, 4, 6]`.
For every binary string of the form `'0' * k + '1' * k` or `'1' * k + '0' * k`, the middle of this string must occur between two groups.
Let's try to count the number of valid binary strings between `groups[i]` and `groups[i+1]`. If we have `groups[i] = 2`, `groups[i+1] = 3`, then it represents either `"00111"` or `"11000"`. We clearly can make `min(groups[i], groups[i+1])` valid binary strings within this string. Because the binary digits to the left or right of this string must change at the boundary, our answer can never be larger.
### Algorithm
Let's create `groups` as defined above. The first element of s belongs in it's own group. From then on, each element either doesn't match the previous element, so that it starts a new group of size 1; or it does match, so that the size of the most recent group increases by 1.
Afterwards, we will take the sum of `min(groups[i-1], groups[i]).`






