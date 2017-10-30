# 1-bit and 2-bit Characters

## Descriptions: 
We have two special characters. The first character can be represented by one bit 0. The second character can be represented by two bits (10 or 11).
Now given a string represented by several bits. Return whether the last character must be a one-bit character or not. The given string will always end with a zero.



#### Example1
```
Input: 
bits = [1, 0, 0]
Output: True
Explanation: 
The only way to decode it is two-bit character and one-bit character. So the last character is one-bit character.
```

#### Example2
```
Input: 
bits = [1, 1, 1, 0]
Output: False
Explanation: 
The only way to decode it is two-bit character and two-bit character. So the last character is NOT one-bit character.
```

#### Note
- 1 <= len(bits) <= 1000.
- bits[i] is always 0 or 1.

## My Solution
```
var isOneBitCharacter = function(bits) {
    for(let i = 0; i < bits.length; i++) {
        let bit = bits[i]
        if(bit === 1){
            i++
            continue
        }else if(i === bits.length - 1){
            return true
        }else{
            continue
        }
    }
    
    return false
};
```

## Best Solution🎆
```javascript
var isOneBitCharacter = function(bits) {
    let i = 0
    while(i < bits.length - 1) i+= bits[i] + 1
    return i === bits.length - 1
};
```

## Comments
- My solution is naive.
- Best solution use the fact: 2-bits characters start with 1 and it's length is 2.We just need to make the index add with the current value, will make index move by 1-bit & 2-bits characters.






