# Average of Levels in Binary Tree

## Descriptions: 
Given a non-empty binary tree, return the average value of the nodes on each level in the form of an array.



#### Example 1:
``` 
Input:
    3
   / \
  9  20
    /  \
   15   7
Output: [3, 14.5, 11]
Explanation:
The average value of nodes on level 0 is 3,  on level 1 is 14.5, and on level 2 is 11. Hence return [3, 14.5, 11].
```

#### note:
1. The range of node's value is in the range of 32-bit signed integer.

## My Solution
```
var averageOfLevels = function(root) {
    function levelAverage(nodeList) {
        return nodeList.reduce((prev,current) => {
                    return prev + current.val
               },0) / nodeList.length
    }
    function nextLevelNodes(nodeList) {
        let rst = []
        nodeList.forEach((v) => {
            if(v.left) rst.push(v.left)
            if(v.right) rst.push(v.right)
        })
        return rst
    }
    
    let resultArr = [root.val]
    let currentLevel = nextLevelNodes([root])
    while(currentLevel.length){
        resultArr.push(levelAverage(currentLevel))
        currentLevel = nextLevelNodes(currentLevel)
    }
    return resultArr
};
```

## Another Solution🎆
```javascript
var averageOfLevels = function(root) {
    
    let levels = {};
    let result = [];
    
    var getAverages = (node, level) => {
        
        if (!node) {
            return;
        }
        
        if (!levels[level]) {
            levels[level] = {
                count: 0,
                sum: 0
            }
        }
        
        levels[level].count = levels[level].count + 1;
        levels[level].sum = levels[level].sum + node.val;
        
        getAverages(node.left, level + 1);
        getAverages(node.right, level + 1);
        
    }
    
    getAverages(root, 0);

    let i = 0;
    while (levels[i]) {
        result.push(levels[i].sum / levels[i].count)
        i++;
    }
    
    return result;
    
};
```

## Comments
- Mine is BFS way.
- Another is a DFS way with more time complexity.
 





