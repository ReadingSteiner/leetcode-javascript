# Reverse Words in a String III

## Descriptions: 
Given a string, you need to reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.

Example:
``` 
Input: "Let's take LeetCode contest"
Output: "s'teL ekat edoCteeL tsetnoc"
```

### Note: 		In the string, each word is separated by single space and there will not be any extra space in the string.




## My Solution
```
/**
 * @param {string} s
 * @return {string}
 */
var reverseWords = function(s) {
    return s.split(' ')
            .map(v => v.split('').reverse().join(''))
            .join(' ')
};
```

## Best Solution🎆
```javascript
// I am the BEST
```

## Comments
- This is really a simple problem: split words by space, then reverse the word, and finally join then with space again.






