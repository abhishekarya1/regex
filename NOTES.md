# Running Notes and Test Examples

Regex pronunciation: "Redj-ex"

## Regex in programming languages

C++11 onwards (`<regex>` header), Python, Java, Javascript, PHP, Java, etc...

### C++ 

Regex is written in the form of a string inside double-quotes (`""`)

```cpp
regex foo("Geek[a-zA-Z]+"); //foo is the object of regex 
```
### Javascript & Ruby

Regex is written within forward slashes (`/regex/`)

```js
var str = 'cat';
if (str.match(/a/)) {
  console.log("matched 'a'");
}

if (str.match(/x/)) {
  console.log("matched 'x'");
}
```

## Basic Match
[Example#0](https://www.regexpal.com/?fam=116958)

## Meta Characters
Reserved chars. Use `\` to escape. Ex - `\.`, `*`, etc...

### Dot `.`
Matches a single character only (except newline char `\n`)<br><br>
[Example#0](https://www.regexpal.com/?fam=116959)<br>
[Example#1](https://www.regexpal.com/?fam=116960)
  
### Character Set
aka Character Class<br><br>
Specified inside square brackets `[]`
  - No Space : [Example#0](https://www.regexpal.com/?fam=116961)
  - Hyphen : [Example#1](https://www.regexpal.com/?fam=116971)
  
A dot `.` inside a Char class means a literal dot `.`
  - [Example#0](https://www.regexpal.com/?fam=116963)
  - [Example#1](https://www.regexpal.com/?fam=116964)
  
### Negated Character Sets
Any char/charset written within `[]` and preceded by `^` will be negated.
  - `[^c]ar` : [Example#0](https://www.regexpal.com/?fam=116965)
  - `[^ctpj]` : [Example#1](https://www.regexpal.com/?fam=116966)
  
### Repetitions
Symbols `*`, `+`, and `?`
  - Asterisk `*` : No. of occurances of char/charset preceding it must be >=0 
    - On single char : [Example#0](https://www.regexpal.com/?fam=116967)
    - On charset : [Example#1](https://www.regexpal.com/?fam=116968)
    
  - Plus `+` : No. of occurances of char/charset preceding it must be >=1
    - On single char : [Example#0](https://www.regexpal.com/?fam=116969)
    - On charset : [Example#1](https://www.regexpal.com/?fam=116970)
    
  - Question Mark `?`
    - Makes the preceding character optional.It matches zero or one instance of the preceding character. If character is there, it matches whole word, if not, then it matches remainning word other than optional char. 
    - [Example#0](https://www.regexpal.com/?fam=116974)

### Braces
aka Quantifiers, wrritten only post char/charset.<br><br>
Can be applied to both Char and Charset<br><br>
Usage Styles : `{n1,n2}`, `{n1,}`, `{n}`

### Capturing Groups
Uses`()` to create a match and capture the chars together. Ex - `(ab)*`<br><br>
Can use altenations inside of it as `(c|r|m|e|f)at`<br><br>
[Example#0](https://www.regexpal.com/?fam=116976)

### Non-Capturing Groups
Uses `?` followed by a `:` within `()` to create a match but not capture the chars. Ex - `(?:c|r|m|e|f)at`

### Alternation `|`
Works like logical OR operator
<details>
  <summary>Question: Isn't [Tt]he same as (T|t)he?</summary>
  
  Ans: In the above case it's the same. But, alternations work at expression level and charset at char level only.
  We can alter between expressions using `|` as `abhi(shek|manyu)` but not as `abhi[shekmanyu]`.
  
</details> 

### Escaping Special Characters
Prepend a special char with a backslash `\` to use it as a matching char.

### Anchors
Caret `^` and Dollar `$`
- Caret `^` used to specify start symbol of the input string. Ex - String that starts with T is matched by `^T`
- Dollar `$` used to specify terminating symbol of the input string. Ex - String that ends with e is matched by `e$`

### Shorthand Character Sets
|Shorthand|Description|
|:----:|----|
|.|Any character except new line|
|\w|Matches alphanumeric characters: `[a-zA-Z0-9_]`|
|\W|Matches non-alphanumeric characters: `[^\w]`|
|\d|Matches digits: `[0-9]`|
|\D|Matches non-digits: `[^\d]`|
|\s|Matches whitespace characters: `[\t\n\f\r\p{Z}]`|
|\S|Matches non-whitespace characters: `[^\s]`|
