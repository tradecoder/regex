# regex
Understanding use of regex methods.

1. **[.test() method](#test-method)**
* [Plain search (Case sensitive / insensitive)](#plain-search-with-test-method)
* [Conditional search with Or `|` operator](#conditional-search-with-or--operator-with-test-method)
2. **[.match() method](#match-method)**



## .test() method
Test method returns true/false.
In this method Content of String to pass inside the test().  
`Regex.test("Content of String")` 

### Plain search with .test() method
* Regex with case sensitive and find a match with a whole word.

```javascript
let myText = "Yes it is";
let myRegex = /Yes/;
let result = myRegex.test(myText);
//true

let anotherRegex = /yes/;
let anotherResult = myRegex.test(anotherRegex);
// false
```
* Regex with case insensitive and find a match with a whole word
* To make it add an `i` at the end of regex. Here `i` is 'ignore case'.

```javascript
let myText = "Yes it is";
let anotherRegex = /yes/i;
let anotherResult = anotherRegex.test(myText);
//true
```

### Conditional search with 'Or' `|` operator with .test() method
Here regex will return true if any of the given word matches

```javascript
let myText = "Yes, it is okay";
let myRegex = /yes|no|okay/;
let result = myRegex.test(myText);
// true . for matching one of the items 'okay'

```


## .match() method
In this method regex to pass inside the match(). It returns the word searching for if matched (full or partial from the begining), otherwise null

`"String".match(/regexHere/)`
### Return single word with .match() method
```javascript
let myText = "Yes it is";
let myRegex = /Yes/;
let result = myText.match(myRegex)
// returns "Yes"

```
### Return all words with .match() method
Just add `g` flag at the end of the regex. It will return all the matched words in an array.

```javascript
let myText = "Yes it is. Yes, it works";
let myRegex = /Yes/g;
let result = myText.match(myRegex);
// returns ["Yes", "Yes"]
```

### Using `g` and `i` flag together
This will search for multiple match (global) and case insensitive (ignoreCase).

```javascript
let myText = "Yes, it is, yes, it works";
let myRegex = /Yes/gi;
let result = myText.match(myRegex);
// returns ["Yes", "yes"]
```

