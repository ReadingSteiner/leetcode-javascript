# Reshape the Matrix

## Descriptions: 
In MATLAB, there is a very useful function called 'reshape', which can reshape a matrix into a new one with different size but keep its original data.
You're given a matrix represented by a two-dimensional array, and two positive integers r and c representing the row number and column number of the wanted reshaped matrix, respectively.
The reshaped matrix need to be filled with all the elements of the original matrix in the same row-traversing order as they were.
If the 'reshape' operation with given parameters is possible and legal, output the new reshaped matrix; Otherwise, output the original matrix


Example 1:
``` 
Input: 
nums = 
[[1,2],
 [3,4]]
r = 1, c = 4
Output: 
[[1,2,3,4]]
Explanation:
The row-traversing of nums is [1,2,3,4]. The new reshaped matrix is a 1 * 4 matrix, fill it row by row by using the previous list.
```

Example 2:
``` 
Input: 
nums = 
[[1,2],
 [3,4]]
r = 2, c = 4
Output: 
[[1,2],
 [3,4]]
Explanation:
There is no way to reshape a 2 * 2 matrix to a 2 * 4 matrix. So output the original matrix.
```

### Note:
1. The height and width of the given matrix is in range [1, 100].
2. The given r and c are all positive.



## My Solution
```
var matrixReshape = function(nums, r, c) {
    let nr = nums.length
    let nc = nums[0].length
    // return origin matrix
    if(r*c !== nr * nc)
        return nums
    
    let rst = []
    for(let i = 0; i < r; i++) {
        rst[i] = []
        for(let j = 0; j < c; j++){
            // index @ one dimension 
            let position1d = i*c + j + 1
            
            // base
            let baseRow = Math.floor(position1d / nc)
            let offset = position1d % nc
            
            let positionNR,postionNC
            if(offset === 0) {
                positionNR = baseRow - 1
                positionNC = nc - 1
            }else{
                positionNR = baseRow
                positionNC = offset - 1
            }

            rst[i][j] = nums[positionNR][positionNC]
        }
    }
    
    return rst
};
```

## Best Solution🎆
```javascript
var matrixReshape = function(nums, r, c) {
    let nr = nums.length
    let nc = nums[0].length
    if(r*c !== nr * nc)
        return nums
    
    let rst = [],count = 0
    for(let i = 0; i < r; i++) {
        rst[i] = []
        for(let j = 0; j < c; j++){
           rst[i][j] = nums[Math.floor(count/nc)][count % nc]
           count++
        }
    }
    
    return rst
};
```

## Comments
- My idea is ok, has the best time complexity and space complexity, however my code is little bit awkward, I didn't think the math relationship well.
- The core idea is use turn one martix in to one dimension, and then put into another matrix.You can simply use one loop with directly assignment to achieve this.
- The best solution is also build by me, it is my second code, and this time I finally came out the math relationship through the `count` variable.(After check the Code Sultion though xD)






