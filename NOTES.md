# Running Notes and Test Examples

- Regex pronunciation: "Redj-ex"

## Regex in programming languages
- C++11 onwards (\<regex\> header), Python, Java, Javascript, PHP, Java, etc...

### C++ 
- Regex is written in the form of a string inside double-quotes (""). 
```cpp
regex foo("Geek[a-zA-Z]+"); //foo is the object of regex 
```
### Javascript & Ruby
- Regex is written within forward slashes (/regex/).
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
- [Example#0](https://www.regexpal.com/?fam=116958)

## Meta Characters

### Dot `.`
- Matches a single character only (except newline char `\n`)
  - [Example#0](https://www.regexpal.com/?fam=116959)
  - [Example#1](https://www.regexpal.com/?fam=116960)
  
### Character Set
- aka Character Class
- Specified inside square brackets `[]`
  - No Space : [Example#0](https://www.regexpal.com/?fam=116961)
  - Hyphen : [Example#1](https://www.regexpal.com/?fam=116971)
- Dot `.` inside a Char class means a literal dot `.`
  -[Example#0](https://www.regexpal.com/?fam=116963)
  -[Example#1](https://www.regexpal.com/?fam=116964)
  
### Negated Character Sets
- Any char/charset written within `[]` and preceded by `^` will be negated.
  - `[^c]ar` : [Example#0](https://www.regexpal.com/?fam=116965)
  - `[^ctpj]` : [Example#1](https://www.regexpal.com/?fam=116966)
  
### Repetitions
- Symbols `*`, `+`, and `?`
  - Asterisk `*` : No. of occurances of char/charset preceding it must be >=0 
    - On single char : [Example#0](https://www.regexpal.com/?fam=116967)
    - On charset : [Example#1](https://www.regexpal.com/?fam=116968)
    
  - Plus `+` : No. of occurances of char/charset preceding it must be >=1
    - On single char : [Example#0](https://www.regexpal.com/?fam=116969)
    - On charset : [Example#1](https://www.regexpal.com/?fam=116970)
    
  - Question Mark `?`
    - 
