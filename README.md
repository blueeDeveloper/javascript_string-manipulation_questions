# Javascript String Manipulation Questions 

1) Count vowels and consonants.

```
const countVowelsConsonants = (str) => {
    const vowelCount = str.match(/[aeiou]/gi) || [];
    const consonantCount = str.match(/[bcdfghjklmnpqrstvwxyz]/gi) || []
    
    return {
        vowel: vowelCount.length,
        consonant: consonantCount.length
    } 
}
let res = countVowelsConsonants("Hello World!! 2026");
console.log(res)
```

/[aeiou]/gi: This is a Regular Expression.
The g flag means "global" (find all matches, not just the first). The i flag means "insensitive" (match both 'A' and 'a') .match(): This returns an array of every character that fits the description.
|| []: This is a "short-circuit." If the string has zero vowels, .match() returns null. Adding || [] ensures we get an empty array instead, so that calling .length doesn't crash your code.


```
const countVowelConsonants = (str) => {
    const vowelList = 'aeiou';
    let res = {
        vowelCount: 0,
        consonantsCount: 0
    }
    for (let char of str) {
        if ((/[a-z]/i).test(char)) {
            if (vowelList.includes(char.toLowerCase())) {
                res.vowelCount++
            } else {
                res.consonantsCount++
            }
        }
    }

    return res;
}

let res = countVowelConsonants('Hello World 2026!!!')
console.log(res)
```



2) Find the first non-repeated character.

  ```
  const findNonRepeatedChar = (str) => {
    const obj = {}
    for (let char of str) {
        obj[char] = (obj[char] || 0) + 1
    }
    for (let char of str) {
        if (obj[char] === 1) {
            return char
        } else return null
    }
}
let res1 = findNonRepeatedChar('asq')
let res2 = findNonRepeatedChar('aabbcc')
console.log(res1, res2)
```

```
const findNonRepeatedChar = (str) => {
    let result = str.split('').find(char => str.indexOf(char) === str.lastIndexOf(char)) || null;
    return result
}
let res1 = findNonRepeatedChar('asq')
let res2 = findNonRepeatedChar('aabbcc')
console.log(res1, res2)
```



3) Remove duplicate characters from a string.

using Set
```
const removeDuplicateChars = (str) => {
    let result = [...new Set(str)].join('')
    return result
}
let result = removeDuplicateChars('assq')
console.log(result)
```

without using Set
```
const removeDuplicateChars = (str) => {
    let res = str.toLowerCase().split('').filter((char, index) => {
        return str.indexOf(char) === index
    }).join('')
    return res;
}
let result = removeDuplicateChars('aAAsssq')
console.log(result)
```

4) Check if two strings are Anagrams.

```
const strictAnagram = (str1, str2) => {
    if (str1.length !== str2.length) return false
    let charMap = new Map()
    for (let char of str1) {
        charMap.set(char, (charMap.get(char) || 0) + 1)
    }
    
    for(let char of str2) {
        if (!charMap.has(char) || charMap.get(char) === 0) {
            return false
        }
        charMap.set(char, charMap.get(char) - 1)
    }
    return true
}
console.log(strictAnagram("Node.js!", "!js.deNo")); // true
```

   
5) Count the occurrence of a specific character.

three ways to do it. traditional for loop, using reduce and split trick


   
6) Check if a string contains only digits.
   
7) Find the first repeated character in a string.
    
8) Check if a string is a rotation of another string.
    
9) Find all permutations of a string.
    
10) Find all substrings of a string.
    
11) Check if a string has all unique characters.
    
12) Remove all whitespace from a string.
    
13) Replace a specific character with another.
    
14) Find the longest word in a sentence.
    
15) Check if two strings are isomorphic.

16) Count the number of words in a sentence.
    
17) Reverse each word in a given sentence.
