# Merge Two Binary Trees

## Descriptions: 
Given two binary trees and imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not.

You need to merge them into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of new tree.

Input:
``` 
	Tree 1                     Tree 2                  
          1                         2                             
         / \                       / \                            
        3   2                     1   3                        
       /                           \   \                      
      5                             4   7                  
Output: 
Merged tree:
	     3
	    / \
	   4   5
	  / \   \ 
	 5   4   7
```


### My Solution
```
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} t1
 * @param {TreeNode} t2
 * @return {TreeNode}
 */
var mergeTrees = function(t1, t2) {
    function merge(target,t1node,t2node){
        if(!t1node && !t2node){
            return null
        }else if(!t1node && t2node) {
            return t2node
        }else if(!t2node && t1node) {
            return t1node
        }else {
            if(!target) target = new TreeNode(0)
            target.val = (t1node.val || 0) + (t2node.val || 0)
            if(t1node.left || t2node.left){
                target.left = merge(target.left, t1node.left, t2node.left)    
            }
            if(t1node.right || t2node.right){
                target.right = merge(target.right, t1node.right, t2node.right)        
            }
            
            return target
        }
    }
    return merge(null,t1,t2)
};
```

## Best Solution🎆
```javascript
var mergeTrees = function(t1, t2) {
    var root = null
    if (t1 && t2) {
        root =  new TreeNode(null);
        root.val = (t1.val) + (t2.val);
        root.left = mergeTrees(t1.left, t2.left);
        root.right = mergeTrees(t1.right, t2.right);
    } else if (t1) {
        root = t1
    } else if (t2){
        root = t2
    } 
    return root;
};
```

## Comments
- My solution is has two awkward place:
	- I should use function `mergeTrees` itself to do the recursion.It is really stupid to build another function inside it.
	- I should judge the `t1 && t2` first, so I don't need to judge bunches of conditions.
- The best solution is very easy to learn, but I know it really takes time to be such simple.






