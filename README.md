# Regex Tutorial

Regular expression (Regex for short) is a sequence of characters that specifies a search pattern in text. Regex is widely support by many programming languages, including JavaScript, C, C++, Java, Rust, OCaml, and Python. It is a very useful tool for web developers just like you.

## Summary

In this tutorial, we will go through some specifics of regex so that we can understand the search pattern that regex defines. Usually such patterns are used by string-searching algorithms for "find" or "find and replace" operations on strings, or for input validation. Regular expression techniques are developed in theoretical computer science and formal language theory.
Here is an example of regex to match an email address:

`/^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+$/`

The following content will explain what each section of regex.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

/`^`[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+`$`/

Anchors do not match any chararcters at all. Instead, they match a position before, after or between chararcters. They were used to "anchor" the regex match a certain position. 
The caret `^` matches the position before the first character in the string. For example, ^a to abc matches the first character of the string abc. But ^b to abc does not match the second letter b in string abc, because the character b is not the first character of string abc. 

### Quantifiers

Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found.
The simplest quantifier is a number in curly braces: `{n}`

* The exact count: `{3}`
`\d{3}` denotes exactly 3 digits, the same as \d\d\d.
* The range: `{2,4}`, match 2-4 times. The uppper limit can be omitted.  Then a regexp `\d{2,}` looks for sequences of digits of length 2 or more.
#### shorthands
There are also some shorthands which represent `{m,n}`
* `+` Means "one or more", which is the same as `{1,}`.
* `?` Means "zero or one", which is the same as `{0,1}`.
* `*` Means "zero or more", which is the same as `{0,}`.

For examples: `alert( "0 1 12.345 7890".match(/\d+\.\d+/g) )`; `// 12.345`
### OR Operator
Alternation is the term in regular expression that is actually a simple “OR”. In a regular expression it is denoted with a vertical line character `|`.
For instance, if we need to find words html, php, java, or java(script) in a string, we can use the following codes: 
let regexp = /html`|`php`|`css`|`java(script)?/gi;
let str = "First HTML appeared, then CSS, then JavaScript";
alert( str.match(regexp) ); // 'HTML', 'CSS', 'JavaScript'
* use with parentheses. The OR operator can be used with parathese.

For example:

`I love HTML| CSS` matches `I love HTML` or `CSS`.

`I love (HTML|CSS)` matches `I love HTML` or `I love CSS`.

### Character Classes

Character classes distinguish kinds of characters. For example, distinguishing between letters and digits.


* `[ABC]` Characters inside brakets will match any character in the set. Both `[abcd-]` and `[-abcd]` match the "`"(hyphen) in "non-profit".
* `[a-d]` which is the same as `[abcd]`. They match the "b" in "brisket". 
* `[^xyz]` The "^" inside the bracket means not. In this case, it matches all the character which is not x, y or z. 
* `\d` Matches any digit character (0-9)
* `\D` Matches andy character that is not a digt. It equivalents to `[^0-9]`.
* `\w` Matches any alphanumeric character from the basic Latin alphabet, in cluding the underscore. It is the same as`[a-zA-Z0-9_]`.
* `\W` Matches any character that is not a word character from the basic Latin alphabet. It equivalents to `[^A-Za-z0-9_]`.
*  `.` Matches any single characterexpect linebreaks. For example: `/.y/` matches "my" and "ay", but not "yes", in "yes make my day".
* `\s` Matches a single white space character, including space, tab, form feed, line feed, and other Unicode spaces. For example, `/\s\w*/` matches " bar" in "foo bar".

* `\S` Matches a single character other than white space. For example, `/\S\w*/` matches "foo" in "foo bar".

### Flags
In Regex, flags are used to define the search.
* `i` with this flag, the search won't care about capital letter or lowercase.
* `g` with this flag, the search will return all matches in the request sting. Without it, only the first match will be returned. 
* `m` Means multiline mode. 
* `s` Enables "dotall" mode, that allows a dot `.` to match newline character `\n`.
* `u` Enables full Unicode supprot. 
* `y` Is for "Sticky" mode, which searches at the exact position in the text. 

### Grouping and Capturing



### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
