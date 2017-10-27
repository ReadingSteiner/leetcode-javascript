# Trim a Binary Search Tree

## Descriptions: 
Given a binary search tree and the lowest and highest boundaries as L and R, trim the tree so that all its elements lies in [L, R] (R >= L). You might need to change the root of the tree, so the result should return the new root of the trimmed binary search tree.

#### Example1
```
Input: 
    1
   / \
  0   2

  L = 1
  R = 2

Output: 
    1
      \
       2
```

#### Example2
```
Input: 
    3
   / \
  0   4
   \
    2
   /
  1

  L = 1
  R = 3

Output: 
      3
     / 
   2   
  /
 1
```

## My Solution
```
var trimBST = function(root, L, R) {
    if(!root) return null
    if(root.val >= L && root.val <= R) {
        root.left && (root.left = trimBST(root.left, L, R))
        root.right && (root.right = trimBST(root.right, L, R))
    }else if(root.val < L) {
        root = trimBST(root.right, L, R)
    }else {
        root = trimBST(root.left, L, R)
    }
    
    return root
};
```

## Best Solution🎆
```javascript
My solution is good.
```

## Comments
- firstly we check if this node is `L <= val <= R`, if so ,we do the recursion for its' left & right node.
- if `val < L`, which means we should use the right node to replace this node. The another situtaion is the same logic.





