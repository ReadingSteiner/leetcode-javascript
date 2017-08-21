# Island Perimeter

## Descriptions: 
You are given a map in form of a two-dimensional integer grid where 1 represents land and 0 represents water. Grid cells are connected horizontally/vertically (not diagonally). The grid is completely surrounded by water, and there is exactly one island (i.e., one or more connected land cells). The island doesn't have "lakes" (water inside that isn't connected to the water around the island). One cell is a square with side length 1. The grid is rectangular, width and height don't exceed 100. Determine the perimeter of the island.


Example 1:
``` 
[[0,1,0,0],
 [1,1,1,0],
 [0,1,0,0],
 [1,1,0,0]]

Answer: 16
Explanation: The perimeter is the 16 yellow stripes in the image below:
```
![](https://leetcode.com/static/images/problemset/island.png)

## My Solution
```
var islandPerimeter = function(grid) {
    let row = grid.length
    let col = grid[0].length
    let perimeter = 0
    let map = {}
    for(let i = 0; i < row; i++){
        for(let j = 0; j < col; j++){
            if(grid[i][j] === 1) {
                map[`${i}-${j}`] = 1
                let tempPerimeter = 4
                // left
                if(map[`${i-1}-${j}`] === 1){
                    perimeter--
                    tempPerimeter--
                }
                // top    
                if(map[`${i}-${j-1}`] === 1){
                    perimeter--
                    tempPerimeter--
                }
                
                perimeter += tempPerimeter
            }
        }
    }
    return perimeter
};
```

## Best Solution🎆
```javascript
var islandPerimeter = function(grid) {
    let neighbors = 0
    let islands = 0
    for(let i = 0; i < grid.length; i++){
        for(let j = 0; j < grid[0].length; j++){
            if(grid[i][j] === 1) {
                islands++
                // left
                if(grid[i-1] && grid[i-1][j] === 1){
                    neighbors++
                }
                // top    
                if(grid[i][j-1] === 1){
                    neighbors++
                }
            }
        }
    }
    return islands*4 - neighbors*2
};
```

## Comments
- My idea is ok, but using template string is time wasting.
- The best solution is more intuitive, it caculate the island num and neighbor num, and finally caculate the perimeter.
 





