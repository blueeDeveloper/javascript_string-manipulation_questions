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

Split Trick 
```
const charOccuranceCount = (str, charToCount) => {
   let count = str.split(charToCount).length-1
   return count
}
console.log(charOccuranceCount("Javascript is awesome", "a")); //Count-3
```

Traditional for loop

```
const charOccuranceCount = (str, charToCount) => {
    let count = 0;
   for (let char of str) {
       if(char === charToCount) count ++
   }
   return count
}
console.log(charOccuranceCount("Javascript is awesome", "a")); //Count-3
```

Using Reduce - NOTE: we have to use ++acc here instead of acc++ otherwise acc++ will return its original value 0 

```
const charOccuranceCount = (str, charToCount) => {
    let count = [...str].reduce((acc, currentChar) => {
      return currentChar === charToCount ? ++acc: acc;  
        
    }, 0 );
    
    
    return count
}
console.log(charOccuranceCount("Javascript is awesome", "a")); //Count-3
```

   
6) Check if a string contains only digits.

Regex approach

```
const isNumeric = (str) => /^-?\d*\.?\d+$/.test(str);
```

<img width="723" height="439" alt="Screenshot 2026-02-25 at 11 56 12 AM" src="https://github.com/user-attachments/assets/8dc6bc4a-a575-4e5f-9efa-0ea8af97e2c6" />

 
7) Find the first repeated character in a string.

There are two ways we can do this. Brute Force method and using Set

Bruce Force Method

```
const findFirstRepeatedChar = (str) => {
    for(let i=0; i < str.length; i++) {
        for(let j=0; j <i; j++) {
            if(str[i]=== str[j]) {
                return str[i]
            }
        }
    }
    return null
    
}
console.log(findFirstRepeatedChar("google")); // result- o
```

Using Set() 

```
const findFirstRepeatedChar = (str) => {
    let currSet = new Set();
    for (const char of str) {
        if(currSet.has(char)) return char
        else currSet.add(char);
    }
    return null
    
}
console.log(findFirstRepeatedChar("google")); // result- o

```

    
8) Check if a string is a rotation of another string.

```
const isRotationManual = (str1, str2) => {
   if(str1.length !== str2.length || str1.length === 0) return false
   
   const concatenatedStr = str1 + str1;
   return concatenatedStr.includes(str2)
    
}
console.log(isRotationManual("stack", "cksta")); // result- true
```


    
9) Find all permutations of a string.
    
10) Find all substrings of a string.
    
11) Check if a string has all unique characters.

```
const hasAllUniqueChars = (str) => {
   const charSet = new Set(str)
   return charSet.size === str.length
}
console.log(hasAllUniqueChars("stack")); // result- true
console.log(hasAllUniqueChars("google")); // result- false
```
    
12) Remove all whitespace from a string.

```
const removeWhiteSpaces = (str) => {
  const strWithoutSpaces = str.replace(/\s+/g, '')
  return strWithoutSpaces
}

console.log(removeWhiteSpaces("Hello, World!")); 
```

13) Replace a specific character with another.

can be implemented in 3 ways - using replaceAll and replace and regular expressions
```
let text = "apple pie";
let newText = text.replaceAll("p", "b"); //Result - "abble bie"
let newText2 = text.replace("p", "b"); //Result - "abple pie"
let newText3 = text.replace(/p/gi, 'b') //Result - "abble pie" 
```

    
14) Find the longest word in a sentence.
Can be implemented in two ways, for of loop and reduce

1. Using for...of loop

```
const findLongestWord = (str) => {
  let words = str.split(" ");
  let longestWord = "";
  
  for(let word of words) {
    if(word.length > longestWord.length) {
      longestWord = word;
    }
  }
  return longestWord;
}
console.log(findLongestWord("This is my time to shine")); //shine
```

Using reduce 

```
const findLongestWord = (str) => {
  return str.split(' ').reduce((longest, current) => {
    return current.length > longest.length ? current : longest;
  }, "");
};

const sentence = "The quick brown fox jumped over the lazy dog";
console.log(findLongestWord(sentence)); // "jumped"
```
    
15) Check if two strings are isomorphic.


16) Count the number of words in a sentence.

```
const countWords = (str) => {
  const words = str.trim().split(/\s+/);
  
  return words[0] === '' ? 0 : words.length;
};

// Test cases
console.log(countWords("Hello world"));        // 2
console.log(countWords("   Too   many   spaces ")); // 3
console.log(countWords(""));                   // 0
console.log(countWords("\n Newline count"));   // 2
```
    
17) Reverse each word in a given sentence.

const reverseWords = (sentence) => {
  return sentence
    .split(' ') // Split sentence into words
    .map(word => {
      // Split word into chars, reverse them, join back to a word
      return word.split('').reverse().join('');
    })
    .join(' '); // Join words back into a sentence
};

// Examples
console.log(reverseWords("Hello World"));     // "olleH dlroW"
console.log(reverseWords("JavaScript is fun")); // "tpircSavaJ si nuf"


