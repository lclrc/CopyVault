[Chinese](https://github.com/lclrc/CopyVault/blob/main/README.md) | English

# CopyVault

## Script (JavaScript)

**Require:**
- The script should contain at least one main function that can accept one parameter. When executed, the text content will be passed as a parameter to the main function
- Return value of the main function: can be a string or an array of strings. When returning an array of strings, all strings in the array will be displayed as options to choose from

**PR Welcome**

### Reverse Text

For example: the original text is `Hello World`, the output will be `dlroW olleH`

```js
function main(str) {
    return str.split('').reverse().join('');
}
```

### Split by Line Break

For example: the original text is:
```
Hello
World
```
A selection box will pop up, with the text inside being `Hello` and `World` respectively.

This can be used to save multiple related pieces of information in one record, and the separator can be customized.

```js
function main(str) {
    arr = str.split("\n");
    arr.forEach((item, index)=>{
      if(!item){
          arr.splice(index, 1);
      }
    })
    return arr;
}
```

### Convert to MD Project List
For example: the original text is `Hello World`, the output will be `- Hello World`

```js
function main(str) {
    const bullet = '-';
    return `${bullet} ` + str.split(/\r?\n/).join(`\n${bullet} `);
}
```

### Convert GitHub Raw Link
For example: the original text is `https://raw.githubusercontent.com/lclrc/CopyVault/main/README_EN.md`, the output will be `https://github.com/blob/lclrc/CopyVault/main/README_EN.md`

```js
function main(url) {
  // Process the string, replacing "raw.githubusercontent.com" with "github.com/blob"
  const processedUrl = url.replace("raw.githubusercontent.com", "github.com/blob");
  // Create a string array
  const urls = [];
  // Add the processed string to the array
  urls.push(processedUrl);
  // Return the string array
  return urls;
```

### Convert to Uppercase
For example: The original text is `Hello World`, the output will be `HELLO WORLD`

```js
function main(str) {
  // Create a string array
  const strs = [];
  // Process the string, convert to uppercase
  const processedStr = str.toUpperCase();
  // Add the processed string to the array
  strs.push(processedStr);
  // Return the string array
  return strs;
}
```

### Remove All Spaces
For example: The original text is `Hello World`, the output will be `HelloWorld`

```js
function main(str) {
  // Create a string array
  const strs = [];
  // Process the string, remove all spaces
  const processedStr = str.replace(/\s/g, "");
  // Add the processed string to the array
  strs.push(processedStr);
  // Return the string array
  return strs;
}
```

### Remove Leading and Trailing Spaces
For example: The original text is `  Hello World `, the output will be `Hello World`

```js
function main(str) {
  // Create a string array
  const strs = [];
  // Process the string, remove leading and trailing spaces
  const processedStr = str.trim();
  // Add the processed string to the array
  strs.push(processedStr);
  // Return the string array
  return strs;
}
```
