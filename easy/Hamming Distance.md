# Hamming Distance

## Descriptions: 
The Hamming distance between two integers is the number of positions at which the corresponding bits are different.

Given two integers x and y, calculate the Hamming distance.

Note:
0 ≤ x, y < 2^31

Example: 
>Input: x = 1, y = 4
>
Output: 2
>
Explanation:
1   (0 0 0 1)
4   (0 1 0 0)
-----? ---?
>
The above arrows point to positions where the corresponding bits are different.

## My Solution
```javascript
var hammingDistance = function(x, y) {
    return (x ^ y)
           .toString(2)
           .split('')
           .reduce((prev,now) => {return Number(prev) + Number(now)}, 0)
};
```

## Best Solution🎆
```javascript
var hammingDistance = function(x, y) {
    return (x ^ y).toString(2).replace(/0/g, '').length;
};
```

## Comments
- Javascript Bitwise XOR: `a ^ b`
- My thought is: caculate the XOR result of give x and y, and then count the number of `1` of the result in binary.
- The best solution is absolutely better than mine.It just simply replace the all `'0'` to `''`, leaving all `1` in the result string so the `length` === `the count of 1` .



