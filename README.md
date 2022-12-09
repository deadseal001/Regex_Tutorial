# Regex Tutorial

Regular expression (Regex for short) is a sequence of characters that specifies a search pattern in text. Regex is widely support by many programming languages, including JavaScript, C, C++, Java, Rust, OCaml, and Python. It is a very useful tool for web developers just like you.

## Summary

In this tutorial, we will go through some specifics of regex so that we can understand the search pattern that regex defines. Usually, such patterns are used by string-searching algorithms for "find" or "find and replace" operations on strings, or for input validation. Regular expression techniques are developed in theoretical computer science and formal language theory.
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

`^`[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+`$`

Anchors do not match any characters at all. Instead, they match a position before, after or between characters. They were used to "anchor" the regex match a certain position. 
The caret `^` matches the position before the first character in the word. For example, `^a` to abc matches the first character of the word abc. But `^b` to abc does not match the second letter b in word abc, because the character b is not the first character of word abc. 

### Quantifiers

Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found.
The simplest quantifier is a number in curly braces: `{n}`

* The exact count: `{3}`
`\d{3}` denotes exactly 3 digits, the same as `\d\d\d`.
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
* use with parentheses. The OR operator can be used with paratheses.

For example:

`I love HTML| CSS` matches `I love HTML` or `CSS`.

`I love (HTML|CSS)` matches `I love HTML` or `I love CSS`.

### Character Classes

Character classes distinguish kinds of characters. For example, distinguishing between letters and digits.


* `[ABC]` Characters inside brackets will match any character in the set. Both `[abcd-]` and `[-abcd]` match the "`"(hyphen) in "non-profit".
* `[a-d]` which is the same as `[abcd]`. They match the "b" in "brisket". 
* `[^xyz]` The "^" inside the bracket means not. In this case, it matches all the character which is not x, y or z. 
* `\d` Matches any digit character (0-9)
* `\D` Matches any character that is not a digt. It equivalents to `[^0-9]`.
* `\w` Matches any alphanumeric character from the basic Latin alphabet, including the underscore. It is the same as`[a-zA-Z0-9_]`.
* `\W` Matches any character that is not a word character from the basic Latin alphabet. It equivalents to `[^A-Za-z0-9_]`.
*  `.` Matches any single character except linebreaks. For example: `/.y/` matches "my" and "ay", but not "yes", in "yes make my day".
* `\s` Matches a single white space character, including space, tab, form feed, line feed, and other Unicode spaces. For example, `/\s\w*/` matches " bar" in "foo bar".

* `\S` Matches a single character other than white space. For example, `/\S\w*/` matches "foo" in "foo bar".

### Flags
In Regex, flags are used to define the search.
* `i` with this flag, the search will ignore character case.
* `g` with this flag, the search will return all matches in the request sting. Without it, only the first match will be returned. 
* `m` Means multiline mode. 
* `s` Enables "dotall" mode, that allows a dot `.` to match newline character `\n`.
* `u` Enables full Unicode support. 
* `y` Is for "Sticky" mode, which searches at the exact position in the text. 

### Grouping and Capturing
By placing part of a regular expression inside parentheses`()`, you can group that part of the regular expression together. This allows you to apply a quantifier to the entire group or to restrict alternation to part of the regex.

* `(abc)` Capturing groups multiple tokens together and creates a capture group. If there are other Regex after this group, This group must be true before moving on to "match" the next part of the code. Example: The regex `Set(Value)?` matches "Set" or "SetValue". 
* Non-Capturing Groups
 `Set(?:Value)` The question mark and the colon after the opening parenthesis are the syntax that creates a non-capturing group. The matching result of the content in the parenthesis won't be returned.

### Bracket Expressions
A bracket expression is an expression enclosed in square brackets, `[]`. Any individual character between the brackets will match, and you can also use a hyphen to define a set.
For Example: `'elephant'.match(/[abcd]/) // -> matches 'a'`
Caret `^` can also be used inside a bracket expression to negate what is between the brackets. 
For examples: `'donkey'.match(/[^abcd]/) // -> matches 'o'`

### Greedy and Lazy Match
Greedy and lazy match are two searching mode in regex. 
* Greedy mode(default). The quantified character is repeated as many times as possible. The regex search will return the longest possible sting.
    
    For examples:  
    `let regexp = /".+"/g;`  
    `let str = 'a "witch" and her "broom" is one';`  
    `alert( str.match(regexp) ); // "witch" and her "broom"`
* Lazy mode is oposite to greedy mode.It can be enable by putting a question mark '?' after the quantifier. In lazy mode, the Quantified chararcter only repeated the least necessary times.

    For example:   
    `let regexp = /".+?"/g;`  
    `let str = 'a "witch" and her "broom" is one';`  
    `alert( str.match(regexp) ); // "witch","broom"`
### Boundaries

`\b` Is an bondary anchor like the caret `^` and the dollar `$` sign. It matches at a position that is called a “word boundary”.
For examples:   
`let regexp= /\bis\b/;`
`let str='This island is beautiful.';`
`alert( str.match(regexp)); // "is"`  
This "is" is from the word "is" but not from the world "this" or "island" because the word bondary `\b` does not match "h" in world "This" or "l" from world "island".

### Back-references
Back-references are used to match the same text, which was matched by previous capturing group.   
For example:    
`([a-c])x\1x\1` matches axaxa, bxbxb and cxcxc, but not axbxc, or axbxa,
### Look-ahead and Look-behind
Lookahead and lookbehind are zero-length assertions just like the start and end of word anchors. Look-ahead or Look-behind actually matches characters, but only return the match result: match or no match. They only assert whether a match is possible or not. 

* `X(?=Y)` Look-ahead allows you to match X but only if it is followed by Y.

* `(?<=Y)` the pattern match X if there is Y before it.


### References
[REXEGG](https://www.rexegg.com/)   
[ Regular-Expressions.info](https://www.regular-expressions.info/)    
[JavaScript Tutorial: Regular Expression](https://www.javascripttutorial.net/regular-expression-word-boundaries/)
## Author

Wenbo Li, 
Wenbo is a coding lover. He is taking the Rice Univeristy full-stack  BootCamp. Expecting something challenge in the future.


GitHub: [deadseal001](https://github.com/deadseal001)