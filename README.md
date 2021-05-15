# Use of Regex
Understanding use of regex methods.

1. **[Test method - Regex.test(String)](#test-method)**
  * [Plain search (Case sensitive / insensitive)](#plain-search-with-test-method)
  * [Conditional search with Or `|` operator](#conditional-search-with-or--operator-with-test-method)
2. **[Match method - String.match(regex)](#match-method)**
  * [Return single word with .match() method](#return-single-word-with-match-method)
  * [Get all matched words with .match() method](#retrun-all-words-with-match-method)
  * [Get all matched words with .match() method ignoring case](#using-g-and-i-flag-together)
  * [Match all words with wildcard dot](#match-with-wildcard-dot)



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
This will search for multiple match (global) and case insensitive (ignoreCase). <br>
Just add `gi` at the end of the regex.

```javascript
let myText = "Yes, it is, yes, it works";
let myRegex = /Yes/gi;
let result = myText.match(myRegex);
// returns ["Yes", "yes"]
```
### Match with wildcard dot
Using a wildcard dot in regex you can find all the matched word through a pattern. <br>
See these words- dot, don, doc, document, doll, docker... <br>
All are started with common `do` and you can find all the words with a wildcard dot included after `do`<br>
If you add one dot `.` it will continue to one character after the regex word, like `/do./`  will match first two chars and will take additional unknown one char, <br> 
if you add two dots `..` it will match the first two chars for `do` and continue unknow more two chars for two dots `..` and so on.  

```javascript
let myText = "dot, lot, doc, pot, docker";
let myRegex = /do./gi; 
// since we need to search for the whole documents we added a `g` tag and then we wanted to match any case with `i` tag
let result = myText.match(myRegex);
// returns ["dot", "doc", "doc"] 
// for the word docker it finds `do` then takes one more char for one dot `.` so it takes `doc` from docker
```

### Match with options
This type of regex will find words with a fixed begining and a fixed end character but with scopes to select the middle characters from multiple options <br>
The following regex starts to match a word started with `d`, <br>
then searchs for the second character from `[ou]` either `o` or `u` options, <br> 
then finds upto the third character `c`. We also have used `gi` tags to match it global and any case. <br>
So, it will first match `doc`, then `duc` from duck, then it will skip for december because first char is ok but second char not matched as `o` or `u`, then moved to dot and it matched first 2 chars but not the third one `c`. <br>
Finally it will return `doc` and `duc`

```javascript
let myText = "doc, duck, december, dot";
let myRegex = /d[ou]c/gi; 
let searchResult = myText.match(myRegex)
//returns ["doc", "duc"]
```

