# Construct String from Binary Tree

## Descriptions: 
You need to construct a string consists of parenthesis and integers from a binary tree with the preorder traversing way.
The null node needs to be represented by empty parenthesis pair "()". And you need to omit all the empty parenthesis pairs that don't affect the one-to-one mapping relationship between the string and the original binary tree.


#### Example1
```
Input: Binary tree: [1,2,3,4]
       1
     /   \
    2     3
   /    
  4     

Output: "1(2(4))(3)"

Explanation: Originallay it needs to be "1(2(4)())(3()())", 
but you need to omit all the unnecessary empty parenthesis pairs. 
And it will be "1(2(4))(3)".
```

#### Example2
```
Input: Binary tree: [1,2,3,null,4]
       1
     /   \
    2     3
     \  
      4 

Output: "1(2()(4))(3)"

Explanation: Almost the same as the first example, 
except we can't omit the first parenthesis pair to break the one-to-one mapping relationship between the input and the output.
```

## My Solution
```
var tree2str = function(t) {
    if(!t) return ''
    
    if(t.left && t.right){
        return t.val+'('+tree2str(t.left)+')'+'('+tree2str(t.right)+')'
    }else if(t.left){
        return t.val+'('+tree2str(t.left)+')'
    }else if(t. right){
        return t.val+'()'+'('+tree2str(t.right)+')'
    }else{
        return ''+t.val
    }
}
```

## Best Solution🎆
```javascript
My solution is good.
```

## Comments
- Just recursively caculate it.
- Notice that the `val` is number while the output expected to be string.
- The conditions is little bit complicate, so it is not wise to be one-liner.





