# Sum of Two Integers

## Descriptions: 
Calculate the sum of two integers a and b, but you are not allowed to use the operator `+` and `-`.

#### Example1
```
Given a = 1 and b = 2, return 3.
```

#### Example2
```
Input: "10101"
Output: 4
Explanation: There are 4 substrings: "10", "01", "10", "01" that have equal number of consecutive 1's and 0's.
```

## My Solution
```
Sadly I did not came out it.
And I hate bit-wise operation.
```

## Best Solution🎆
```javascript
/**
 * @param {number} a
 * @param {number} b
 * @return {number}
 */
var getSum = function(a, b) {
    while(b !== 0){
        // add two numbers without carry using XOR
        let sum = a ^ b
        // use AND to caculate the carry, assign it to b
        b = (a & b) << 1
        // and the next step is to caculate (sum + carry), which is a + b again
        a = sum
    }
    
    return a
};
```

## Comments
Just check the comments in the best solution.





