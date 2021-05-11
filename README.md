# regex
Understanding regex methods

## .test() method
Test method returns true/false. 
`Regex.test("Content of String")` 

```javascript
let myText = "Yes it is";
let myRegex = /Yes/;
let result = myRegex.test(myText);
//true

let anotherRegex = /yes/;
let anotherResult = myRegex.test(anotherRegex);
// false
```
