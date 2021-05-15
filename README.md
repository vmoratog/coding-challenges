# coding-challenges
Coding challenges with JavaScript

- https://www.hackerrank.com/challenges/2d-array/problem
```js
function hourglassSum(arr) {
    // Write your code here
    let sums = []
    for (let r = 0; r < 4; r++) {
        for (let c = 0; c< 4; c++) {
            sums.push(
                arr[r][c] + arr[r][c+1] + arr[r][c+2]+
                arr[r+1][c+1] + 
                arr[r+2][c] + arr[r+2][c+1] + arr[r+2][c+2])
        }
    }
    return sums.sort((a,b) => b-a)[0]
}
```
