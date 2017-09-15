# Maximum Depth of Binary Tree

## Descriptions: 
Given a binary tree, find its maximum depth.
The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

## My Solution
```
var maxDepth = function(root) {
    let max = 0
    
    const dfs = (node,level) => {
        max = Math.max(max, level)
        if(node.left) dfs(node.left, level+1)
        if(node.right) dfs(node.right, level+1)
    }
    root && dfs(root,1)    
    
    return max
};
```

## Best Solution🎆
```javascript
	var maxDepth = function(root) {
	    if(!root)
	        return 0;
	    return 1 + Math.max(maxDepth(root.left),maxDepth(root.right));
	};
```

## Comments
- I always build another function to do recursion, this is really stupid, I shall never do this again.
- The idea is the same, Depth First Search.
- The best solution is really smart, it describes the truth that the max level of `root` must be the max between `root.left` and `root.right`.This truth is recursivable.
  Each time it enter further, the level will plus one, so when the search reach the leaf node, the level caculation will be done after the final level is checked.





