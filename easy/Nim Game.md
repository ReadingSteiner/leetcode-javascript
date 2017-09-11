# Nim Game

## Descriptions: 
You are playing the following Nim Game with your friend: There is a heap of stones on the table, each time one of you take turns to remove 1 to 3 stones. The one who removes the last stone will be the winner. You will take the first turn to remove the stones.
Both of you are very clever and have optimal strategies for the game. Write a function to determine whether you can win the game given the number of stones in the heap.
For example, if there are 4 stones in the heap, then you will never win the game: no matter 1, 2, or 3 stones you remove, the last stone will always be removed by your friend.


## My Solution
```
// I didn't came out with a solution :(
```

## Best Solution🎆
```javascript
var canWinNim = function(n) {
    return n % 4 !== 0
};
```

## Comments
- Consider when there are only 4 stones. You can never win if you take first because nomatter how much stones(1-3) you take, your friend will always take the last stone.
- Now we have N stones, when the number of stones is divisible by 4, then we can tear the stones into many group of 4 stones, nomatter how much (x) you take every round, your friend can always take 4-x stones  to complete it to 4 stones.
- See? now you can never win this game because it will eventually left 4 stones to your turn, and you lose.
- My IQ is unimaginably decreased after I started working, sad :( .
 





