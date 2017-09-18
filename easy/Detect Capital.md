# Detect Capital

## Descriptions: 
Given a word, you need to judge whether the usage of capitals in it is right or not.
We define the usage of capitals in a word to be right when one of the following cases holds:
	1.	All letters in this word are capitals, like "USA".
	2.	All letters in this word are not capitals, like "leetcode".
	3.	Only the first letter in this word is capital if it has more than one letter, like "Google".
Otherwise, we define that this word doesn't use capitals in a right way.

#### example1
```
Input: "USA"
Output: True
```
#### example2
```
Input: "FlaG"
Output: False
```
#### note:
 The input will be a non-empty word consisting of uppercase and lowercase latin letters.
 
## My Solution
```
var detectCapitalUse = function(word) {
    return /^[A-Z]+$/.test(word) || /^[a-z]+$/.test(word) || /^[A-Z][a-z]+$/.test(word)
};
```

## Best Solution🎆
```javascript
var detectCapitalUse = function(word) {
    return /^[a-z]+$|^[A-Z]+$|^[A-Z][a-z]+$/.test(word)
};
```

## Comments
- Best solution is much more shorter than me.
- I think this kind of problem should be resolve with RegExp.





