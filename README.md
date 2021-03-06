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
Write a function:

function solution(A);

that, given an array A of N integers, returns the smallest positive integer (greater than 0) that does not occur in A.

For example, given A = [1, 3, 6, 4, 1, 2], the function should return 5.

Given A = [1, 2, 3], the function should return 4.

Given A = [−1, −3], the function should return 1.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [1..100,000];
each element of array A is an integer within the range [−1,000,000..1,000,000].

```js
function solution(A) {
    // write your code in JavaScript (Node.js 8.9.4)
    let smallestPositiveInt = 1
    const sortedArrayA = A.sort((a,b)=> a-b) 
    for (let i = 0; i < A.length; i++) {
        if (sortedArrayA[i] > 0) {
            if (smallestPositiveInt === sortedArrayA[i]) {
                smallestPositiveInt++
            } else if ( sortedArrayA[i] > smallestPositiveInt ) {
                break;
            }
        }
    }
    return smallestPositiveInt
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

.https://www.hackerrank.com/challenges/two-strings/problem

```js
function twoStrings(s1, s2) {
    // Write your code here
    let ans = 'NO'

    const strings = s1.length < s2.length? {
        min: s1,
        max: s2
    } : {
        min: s2,
        max: s1
    }
    
    for (let i = 0; i < strings.min.length; i++) {
        const letter = strings.min[i]
        const indexMaxStr = strings.max.indexOf(letter)
        if (indexMaxStr >= 0) {
            ans = 'YES'
            break
        } 
    }
    return ans
}

```

- https://www.hackerrank.com/challenges/ctci-ransom-note/problem

```js
function checkMagazine(magazine, note) {
    // Write your code here

    const dictionaryWords = {}
    let ans = 'Yes'
    
    for(let i= 0; i< magazine.length; i++) {
        const word = magazine[i]
        dictionaryWords[word] = dictionaryWords[word] || 0
        dictionaryWords[word]++
    }
    
    for (let i=0; i < note.length; i++) {
        const word = note[i]
        if (dictionaryWords[word]) {
            dictionaryWords[word]--
        } else {
            ans = 'No'
            break
        }
    }
    console.log(ans)
}

```
