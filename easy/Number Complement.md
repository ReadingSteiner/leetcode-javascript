# Number Complement

## Descriptions: 
Given a positive integer, output its complement number. The complement strategy is to flip the bits of its binary representation.

**Note:**

1.	The given integer is guaranteed to fit within the range of a 32-bit signed integer.
2.	You could assume no leading zero bit in the integer’s binary representation.


Input:
``` 
Input: 5
Output: 2
Explanation: The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.

Input: 1
Output: 0
Explanation: The binary representation of 1 is 1 (no leading zero bits), and its complement is 0. So you need to output 0.

```

### Note: 
1.	n is a positive integer, which is in the range of [1, 10000].
2.	All the integers in the array will be in the range of [-10000, 10000].




## My Solution
```
/**
 * @param {number} num
 * @return {number}
 */
var findComplement = function(num) {
     return parseInt(num.toString(2).split('').map(v => 1-v).join(''), 2)
 };
```

## Best Solution🎆
```javascript
// Solution A
var findComplement = function(num) {
    num = num.toString(2).replace(/[0|1]/g, function (match) {
        return Number(match) ^ 1;
    });
    
    return parseInt(num, 2);
};

// Solution B
var findComplement = function(num) {
    var len = num.toString(2).length
    return Math.pow(2,len) - 1 - num
};

```

## Comments
- My solution is too straight, turn the number into array and reverse it one by one, and then turn it back to string and parse to integer.A REDUNDANT solution.
- Best solution A use the regexp's match function to do the dirty work, same thought with me but more elegant.
	**Note that the `replace` can has a match function to define what can you do to the match part**
- Best solution B is the best way, it uses the feature `111 = 101 + 010`, we just use the 2^n -1 to minus the current number, and then we will get the complement number.






