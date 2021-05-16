# coding-challenges
Coding challenges with JavaScript

- https://www.hackerrank.com/challenges/2d-array/problem
```js
function hourglassSum(arr) {
    // Write your code here
    const sums = []
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

- https://www.hackerrank.com/challenges/ctci-array-left-rotation/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=arrays
```js
function rotLeft(a, d) {
    // Write your code here
    const rotatedArray = new Array(a.length)
    for ( let i = 0; i<a.length; i++) {
       const diff = i-d
       const position = diff < 0? a.length - Math.abs(diff) : diff
       console.log(i, diff, position)
       rotatedArray[position] = a[i]
    }
    console.log(rotatedArray)
    return rotatedArray
}
```
