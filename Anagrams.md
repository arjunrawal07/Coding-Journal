# Anagrams

## Definition: 
A string is considered an anagram if it uses the same characters in the same quantity as another string

## Application: 
* Riddles
* Puzzles
* Mysteries
* Deciphering codes
* Coding Challenges

## Implementation:
### Approach 1: 
```js
 	function anagrams(stringA, stringB) {
		//First, define a function to build a character Map
		function buildCharMap(str) {
     		const charMap = {};
		//Use regular expressions to clean up the string passed in
    	for (let char of str.replace(/[^\w]/g, “”).toLowerCase()) {
				//For every occurence of a character, set its frequency to 1 or add 1 to the existing frequency
     			charMap[char] = charMap[char] + 1 || 1;
    		}
   	return charMap;
		//Build a charMap for strings A and B
     const aCharMap = buildCharMap(stringA);
     const bCharMap = buildCharMap(stringB);

     //Check number of keys in both objects first as a prerequisite
     if (Object.keys(aCharMap).length !== Object.keys(bCharMap).length) {
       return false;
     }
     //iterate over one charMap, look at each char inside, and compare it to the other charMap
    for (let char in aCharMap) {
       if (aCharMap[char] !== bCharMap[char]) {
         return false;
       }
     }
     return true;
   }
}
```

### Approach 2
```js
function anagrams(stringA, stringB) {
	//Call the cleanString helper function on both A and B, and return true only if they are the same
  return cleanString(stringA) === cleanString(stringB);
}

//Build a helper function to clean up a string, make each character lowercase, sort it in ascending order
function cleanString(str) {
  return str.replace(/[^\w]/g, “”).toLowerCase().split(“”).sort().join(“”);
}
```
* Note: The use of Regular Expressions in Approach 2. Regular expressions can be used to manipulate strings. In this case, we remove `“!”` and `“__”` (spaces) because we only want to consider the characters.
	* `\w` is used to match any alpha-numeric character from the basic Latin alphabet. The `g` is for global search. And, we replace any punctuation and spaces found with an empty string.
    * Learn more about RegExp [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions).