# coding-challenges
Coding challenges with JavaScript

## Arrays (level: Easy)

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

- https://www.hackerrank.com/challenges/ctci-array-left-rotation/problem
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

## Sorting (level: easy)

- https://www.hackerrank.com/challenges/ctci-bubble-sort/problem

```js
function countSwaps(a) {
    // Write your code here
    let numSwaps = 0
    const n = a.length
for (let i = 0; i < n; i++) {
    
    for (let j = 0; j < n - 1; j++) {
        // Swap adjacent elements if they are in decreasing order
        if (a[j] > a[j + 1]) {
        let x = a[j]
        a[j] = a[j+1]
        a[j+1] = x
        numSwaps++
        }
    }
}
console.log(`Array is sorted in ${numSwaps} swaps.  
First Element: ${a[0]}
Last Element: ${a[a.length-1]} `)
}
```

- https://www.hackerrank.com/challenges/mark-and-toys/problem

```js
function maximumToys(prices, k) {
    // Write your code here
    let numToys = 0
    let total = 0
    prices = prices.sort((a, b) => a-b)
    for (let i = 0; i < prices.length; i++) {
        const newTotal = total + prices[i]
        if (newTotal <= k) {
            total = newTotal
            numToys++
        } else {
            break
        }
        
    }
    return numToys
}
```
## String Manipulation

- https://www.hackerrank.com/challenges/ctci-making-anagrams/problem

```js
function makeAnagram(a, b) {
    // Write your code here
    const aArray = a.split('')
    const bArray = b.split('')
    const arrays = aArray.length < bArray.length ? {
      min: aArray,
      max: bArray
    } : {
      min: bArray,
      max: aArray
    }
    
    for (let i = 0; i < arrays.min.length; i++) {
        const letter = arrays.min[i]
        const indexMaxLetter = arrays.max.indexOf(letter)
        if (indexMaxLetter >= 0) {
            // Se eliminan las coincidencias
           arrays.min.splice(i, 1)
           arrays.max.splice(indexMaxLetter, 1)
           i-- //retrocedo la posicion que elimine par la siguiente iteración
        }
    }
    // Al eliminar las coincidencias, lo que sobra es lo que no hace parte del anagrama
        return arrays.min.length + arrays.max.length
}
```

- https://www.hackerrank.com/challenges/alternating-characters/problem

```js
function alternatingCharacters(s) {
    // Write your code here
     const str = s.split('')
     let deletedItem = 0
    for (let i = 0; i < str.length; i++) {
        if (str[i] === str[i+1]) {
            str.splice(i, 1)
            deletedItem++
            i--
        }
    }
    return deletedItem
}
```

## Dictionaries and Hashmaps
