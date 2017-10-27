# Max Area of Island

## Descriptions: 
Given a non-empty 2D array grid of 0's and 1's, an island is a group of 1's (representing land) connected 4-directionally (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.
Find the maximum area of an island in the given 2D array. (If there is no island, the maximum area is 0.)


#### Example1
```
[[0,0,1,0,0,0,0,1,0,0,0,0,0],
 [0,0,0,0,0,0,0,1,1,1,0,0,0],
 [0,1,1,0,1,0,0,0,0,0,0,0,0],
 [0,1,0,0,1,1,0,0,1,0,1,0,0],
 [0,1,0,0,1,1,0,0,1,1,1,0,0],
 [0,0,0,0,0,0,0,0,0,0,1,0,0],
 [0,0,0,0,0,0,0,1,1,1,0,0,0],
 [0,0,0,0,0,0,0,1,1,0,0,0,0]]
```
Given the above grid, return 6. Note the answer is not 11, because the island must be connected 4-directionally.

#### Example2
```
[[0,0,0,0,0,0,0,0]]
```
Given the above grid, return 0.

#### Note
 The length of each dimension in the given grid does not exceed 50.

## My Solution
```
var maxAreaOfIsland = function(grid) {
    let maxArea = 0,r=grid.length,c=grid[0].length
    let meetMap = {}
    
    function getAreaFrom(i,j) {
        // 写递归的时候不要在进入下一层之前做判断， 而是在进入下一层之后做判断，逻辑会清晰很多
       if(i >= 0 && i < r && j >= 0 && j < c && meetMap[`${i}-${j}`] !== 1){
           meetMap[`${i}-${j}`] = 1
           if(grid[i][j] !== 0){
                return 1 + getAreaFrom(i-1,j) + getAreaFrom(i,j-1) + getAreaFrom(i+1,j) + getAreaFrom(i,j+1)
           }else{
               return 0
           }
           
       }else{
           return 0
       }
    }
    
    for(let i = 0; i < grid.length; i++) {
        for(let j = 0; j < grid[0].length; j++) {
            if(meetMap[`${i}-${j}`] !== 1){
                maxArea = Math.max(getAreaFrom(i,j),maxArea)
            }
        }
    }
    
    return maxArea
};
```

## Best Solution🎆
```javascript
var traversalDFS = function(grid, i, j, path) {
    if (i >= 0 && i < grid.length && j >= 0 && j < grid[i].length && 1 == grid[i][j]) {
        grid[i][j] = 0;
        path.push([i, j]);
        traversalDFS(grid, i + 1, j, path);
        traversalDFS(grid, i - 1, j, path);
        traversalDFS(grid, i, j + 1, path);
        traversalDFS(grid, i, j - 1, path);
    }
}

var maxAreaOfIsland = function(grid) {
    var max_area = 0;
    for (var i = 0; i < grid.length; i++) {
        for (var j = 0; j < grid[i].length; j++) {
            var path = [];
            traversalDFS(grid, i, j, path);
            if (max_area < path.length)
                max_area = path.length;
        }
    }
    
    return max_area;
};
```

## Comments
- The idea is same: recursively search all the islands and caculate the max area.
- The best solution is much easier to read than mine.
- I used a map to store meeted place while the best solution not.It simply set the all meeted place to `0` to make them not meetable.However this is violating the   immutability.
- The idea of `caculate the path length` is good.






