# Two Sum IV - Input is a BST

## Descriptions: 
Given a Binary Search Tree and a target number, return true if there exist two elements in the BST such that their sum is equal to the given target.

#### Example1
```
Input: 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 9

Output: True
```

#### Example2
```
Input: 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 28

Output: False
```

## My Solution
```
var findTarget = function(root, k) {
    let numbers = []
    let numbersMap = {}
    
    const traverse = (node) => {
        numbers.push(node.val)
        numbersMap[node.val] = 1
        node.left && traverse(node.left)
        node.right && traverse(node.right)
    }
    traverse(root)
    
    for(let i = 0; i < numbers.length; i++){
        if(numbersMap[k-numbers[i]])
            if((k-numbers[i]) !== numbers[i])
                return true
    }
    
    return false
};
```

## Best Solution🎆
```javascript
My solution is not bad, but still need to be improved.
```

## Comments
- Firstly we traverse the tree and build a number map(hashset) and a numbers array for searching.
- Then, we traverse the numbers array, and use the map to check if (k - arr[i]) exsits.
- The wasting place is we traverse the numbers twice, which can be reduced to once.






