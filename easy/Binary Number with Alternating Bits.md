# Binary Number with Alternating Bits

## Descriptions: 
Given a positive integer, check whether it has alternating bits: namely, if two adjacent bits will always have different values.


#### Example1
```
Input: 5
Output: True
Explanation:
The binary representation of 5 is: 101

```

#### Example2
```
Input: 7
Output: False
Explanation:
The binary representation of 7 is: 111.
```

#### Example3
```
Input: 11
Output: False
Explanation:
The binary representation of 11 is: 1011.
```

#### Example4
```
Input: 10
Output: True
Explanation:
The binary representation of 10 is: 1010.
```

## My Solution
```
// solution A
var hasAlternatingBits = function(n) {
    let has = true
    let str = n.toString(2)
    for(let i = 0; i < str.length-1; i++){
        has = has && (str[i]!==str[i+1])
        if(!has) return false
    }
    return true
};

// solution B
var hasAlternatingBits = function(n) {
    let strLen = n.toString(2).length
    return (n^(n>>1)) == (Math.pow(2,strLen)-1)
};
```

## Best Solution🎆
```javascript
The best one is my solution B.
```

## Comments
- Solution A is the naive solution.
- Solution B is quicker and simpler, I didn't came out it, after thinking about XOR bit-wise operator, I find the math relation that n XOR n<<1 must be 111111.... which is `Math.pow(2,x) - 1`. x is the length of the bit string.






