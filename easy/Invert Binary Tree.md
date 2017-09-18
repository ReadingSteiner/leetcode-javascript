# Invert Binary Tree

## Descriptions: 
Invert a binary tree.
```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```
to
```
     4
   /   \
  7     2
 / \   / \
9   6 3   1
```
#### Triva：
This problem was inspired by this original tweet by Max Howell:
> Google: 90% of our engineers use the software you wrote (Homebrew), but you can’t invert a binary tree on a whiteboard so fuck off.

## My Solution
```
var invertTree = function(root) {
    if(!root) return null
    // invert
    let temp = root.left
    root.left = root.right
    root.right = temp
    // recursion
    invertTree(root.left)
    invertTree(root.right)
    
    return root
};
```

## Best Solution🎆
```javascript
var invertTree = function(root) {
    if (root) {
        [root.left, root.right] = [invertTree(root.right), invertTree(root.left)];
    }
    return root;
};
```

## Comments
- I finally finish a recuirsive problem in one function.
- The idea of recursion is the same.
- The best solution is really excellent, it uses the ES2015 destructuring feature to exchange left and right node, reaaaaaally smart.





