# Running Notes and  Examples

Regex pronunciation: *"Redj-ex"*

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
---
## Basic Match
[Example#0](https://www.regexpal.com/?fam=116958)

---
## Meta Characters
Reserved chars. Use `\` to escape. Ex - `\.`, `*`, etc...

---
### Dot `.`
Matches a single character only (except newline char `\n`)<br><br>
[Example#0](https://www.regexpal.com/?fam=116959)<br>
[Example#1](https://www.regexpal.com/?fam=116960)

--- 
### Character Set
aka Character Class<br><br>
Specified inside square brackets `[]`
  - No Space : [Example#0](https://www.regexpal.com/?fam=116961)
  - Hyphen : [Example#1](https://www.regexpal.com/?fam=116971)
  - Both of the above: [Example#2](https://www.regexpal.com/?fam=116994)
  
A dot `.` inside a Char class means a literal dot `.`
  - [Example#0](https://www.regexpal.com/?fam=116963)
  - [Example#1](https://www.regexpal.com/?fam=116964)
  
---  
### Negated Character Sets
Any char/charset written within `[]` and preceded by `^` will be negated.
  - `[^c]ar` : [Example#0](https://www.regexpal.com/?fam=116965)
  - `[^ctpj]` : [Example#1](https://www.regexpal.com/?fam=116995)

---
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

---
### Braces
aka "Quantifiers", written only post char/charset.<br><br>
Can be applied to both Char and Charset<br><br>
Usage Styles : `{n1,n2}`, `{n1,}`, `{n}`

---
### Capturing Groups
Uses`()` to create a match and capture the chars together. Ex - `(ab)*`<br><br>
Can use altenations inside of it as `(c|r|m|e|f)at`: [Example#0](https://www.regexpal.com/?fam=116976)<br><br>
Grouping: [Example#1](https://www.regexpal.com/?fam=116997)

### Non-Capturing Groups
Uses `?` followed by a `:` within `()` to create a match but not capture the chars. Ex - `(?:c|r|m|e|f)at`

---
### Alternation `|`
Works like logical OR operator
<details>
  <summary>Question: Isn't [Tt]he same as (T|t)he?</summary>
  
  Ans: In the above case it's the same. But, alternations work at expression level and charset at char level only.
  We can alter between expressions (multiple-chars/string) using `|` as `abhi(shek|manyu)` but not as `abhi[shekmanyu]`.
  
</details> 

---
### Escaping Special Characters
Prepend a special char with a backslash `\` to use it as a matching char.

---
### Anchors
Caret `^` and Dollar `$`
- Caret `^` used to specify start symbol of the input string. Ex - String that starts with T is matched by `^T`
- Dollar `$` used to specify terminating symbol of the input string. Ex - String that ends with e is matched by `e$`
  - Anchors are expression level. Ex - To look for all files having `.pdf` extensions, we can use: `\.pdf$`

---
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

---
### Word Boundaries
Denoted by `\b`, in most regex dialects, is a position between \w and \W (non-word char), or at the beginning or end of a string if it begins or ends (respectively) with a word character (`[0-9A-Za-z_]`). So, in the string "-12" , it would match before the 1 or after the 2. The dash is not a word character.<br>
[Example#0](https://regex101.com/r/5zYI7K/1)
<br><br>
Note that `^` and `$` are also word boundries as start and end of input respectively.<br>
Also note that `\b`and `\B` matches without consuming any char.
<br><br>
**Non-Word Boundry:**: Matches, without consuming any characters, at the position between two characters matched by `\w`.
<br>[Example#1](https://regex101.com/r/NtXJY8/1)

---
### Backrefernces
When we make a capture group, regex engine references the result implicitly in a first occurance order and we can use that reference with `\ref_num` to use it again. <br>
[Example#0](https://www.regexpal.com/?fam=116999)
<br><br>
Note that capturing is neccessary for backreferening to happen and work.
Also note that backreferences match the same text as most recently matched by the capturing group they reference (i.e. its result) and not the group pattern.<br>
[Example#1](https://regex101.com/r/iMkVk7/1)

**Backreferences to failed groups:** Concept and important distinction [here](https://www.hackerrank.com/challenges/backreferences-to-failed-groups/problem). First example is "b participated but failed, the result was then captured using `()`", second example is "never participated at all" since the entire group was optional, it skipped checking match for `(b)` group altogether.

---
### Branch Reset Groups*
*Branch reset group is supported by Perl, PHP, Delphi and R*
<br><br>
**Syntax:**`(?|(regex1)|(regex2)|(regex3)|.....)`
<br><br>
**Explanation:** It allows us to branch/choose from among `regex1`, `regex2`, `regex3` capture groups, any one, capture the result one time and reference it later on. Note that the `(?|regex)` itself counts as one occurance of the selected single capture group.
<br>
[Example#0](https://www.hackerrank.com/challenges/branch-reset-groups/problem)

---
### Forward References*
*Forward reference is supported by JGsoft, .NET, Java, Perl, PCRE, PHP, Delphi and Ruby*
<br><br>
**Explanation:** It allow you to use a backreference to a group that appears later in the regex. Forward references are obviously only useful if they’re inside a repeated group.<br>
[Example#0](https://www.regular-expressions.info/backref2.html#forward)<br>
[Example#1](https://www.hackerrank.com/challenges/branch-reset-groups/problem)

---
### Lookarounds
Also called "Assertions"
<br>
Two types: **Lookaheads** and **Lookbehinds**
<br>
They are non-capturing
<br>
|Symbol|Name|Description|
|:----:|----|----|
|(?= )|Positive Lookahead|Used on RHS of main regex|
|(?! )|Negative Lookahead|"|
|(?<= )|Positive Lookbehind|Used on LHS of main regex|
|(?<! )|Negative Lookbehind|"|

---
### Flags
Also known as "Modifiers"
<br>Heavily dependent on regex engine being used
<br><br>
|Flag|Description|
|:----:|----|
|i|Case insensitive: Match will be case-insensitive.|
|g|Global Search: Match all instances, not just the first.|
|m|Multiline: Anchor meta characters work on each line. By default, the `$` is at the end of the whole input, but `m` flag forces it at every line end|

---
### Greedy vs Lazy Matching
**Greedy Matching:** Tries to match as much as possible
<br>
Use `?` with any of the six quantifiers to match in a lazy way
<br>
Good explaination [here](https://javascript.info/regexp-greedy-and-lazy).
<br>
Good example [here](https://stackoverflow.com/questions/2301285/what-do-lazy-and-greedy-mean-in-the-context-of-regular-expressions).

---
