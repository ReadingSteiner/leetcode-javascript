# Number Complement

## Descriptions: 
Given a List of words, return the words that can be typed using letters of alphabet on only one row's of American keyboard like the image below.

![](https://leetcode.com/static/images/problemset/keyboard.png)

Example:
``` 
Input: ["Hello", "Alaska", "Dad", "Peace"]
Output: ["Alaska", "Dad"]
```

**Note:** 
1.	You may use one character in the keyboard more than once.
2.	You may assume the input string will only contain letters of alphabet.




## My Solution
```
/**
 * @param {string[]} words
 * @return {string[]}
 */
const row1 = 'QWERTYUIOP'.split('')
const row2 = 'ASDFGHJKL'.split('')
const row3 = 'ZXCVBNM'.split('')

var findWords = function(words) {
    return words.filter(word => {
        let wordUpper = word.toUpperCase()
        let wordFirst = checkRow(wordUpper[0])
        
        for(let i = 1; i < word.length; i++) {
            if(checkRow(wordUpper[i]) !== wordFirst){
                return false
            }  
        }
        
        return true
    })
    
    function checkRow(letter){
        if(row1.indexOf(letter) !== -1)
            return 1
        if(row2.indexOf(letter) !== -1)
            return 2
        return 3
    }
}
```

## Best Solution🎆
```javascript
/**
 * @param {string[]} words
 * @return {string[]}
 */
var findWords = function(words) {
      return words.filter((w) => {
        // remove word from array if it fails matching all three rows
        if (
            !/^[qwertyuiop]*$/i.test(w) &&
            !/^[asdfghjkl]*$/i.test(w) &&
            !/^[zxcvbnm]*$/i.test(w)
        ) return false;
        
        return true;
    });
}
```

## Comments
- The core idea of my solution is: mark each 3 row as `1,2,3`, then I check the words letter by letter.
	Firstly, I check the first letter and get which row it belongs to.
	Then, all the others letter should all belong to the same row, otherwise this is not a `one row word`, return false.
	My solution is very easy to come up with.
	
- The best solution uses the regular expression and the `&&` operator to minimize the caculation.
	It uses 3 regexp to represent 3 kind of `one row word`, and alse uses `&&` operator that can save the caculation —— caculation start from left and once a regexp test failed, the caculation will immediately end.






