# RegEx Tutorial - Email Validation

## This GitHub repository contains a tutorial explaining the use of regular expressions in coding.

## Summary

A regular expression, typically referred to as RegEx or RegExp, is a sequence of characters that specifies a search pattern. Usually such patterns are used by string-searching algorithms for "find" or "find and replace" operations on strings, or for input validation. It is a technique developed in theoretical computer science and formal language theory. [1]

This tutorial will show you how to build a RegEx that checks wether an email address is valid or not.

## Example

A simple example of a RegEx to validate an email input is:

`/\S+@\S+\.\S+/`

A more comprehensive and specific example is:

```/[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*@(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?/g```

---

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

---

## Regex Components

### Anchors: `^` `&` `$`

Anchors are used in several instances - to match a position before, after, or between characters. For example if you tried to match ^S to Start you would get a match, as the string starts with "S". If you were to try and apply ^A to Start, you would not get a match, as the string does not begin with "S".
While ^ can be used to match the start of a string, $ can be used to match the end of a string.

`^Start` matches any string that starts with `Start`.

`^End` matches any string that starts with `End`.

`^Start End$` matches only the string `Start End`.

`information` matches any string that has the text `information` in it.
<br>
<br>
An email doesn't begin or end with any specific character, so we do not need anchors in this example. [2]

---

### Quantifiers: `*` `+` `?` and `{}`

Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found. [3]
<br>

`*` Match zero or more times.

`+` Match one or more times.

`?` Match zero or one time.

`{ x }` Match exactly n times.

`{ x ,}` Match at least n times.

`{ x , y }` Match from n to m times.

*Let's look at our simple example:*

`/\S+@\S+\.\S+/`

This means:
<br>
`\S` `+`
<br>
Match *one or more* of __any__ character.
<br>

`@`
<br>
__Must__ match an __"@"__ symbol.
<br>

`\S` `+`
<br>
Match *one or more* of __any__ character.
<br>

`\.` `+`
<br>
__Must__ match an __"."__ symbol.
<br>

`\S`
<br>
Match *one or more* of __any__ character.

*Now lets look at the comprehensive example:*

```/[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*@(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?/g```

This means:
<br>
<br>
```[a-z0-9!#$%&'*+/=?^_`{|}~-]``` `+`
<br>
Match *one or more* of any the preceding characters within the defined character sets.
<br>
<br>
```(?:.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)``` `*`
<br>
Match *zero or more* of the preceding characters within the defined character sets.
<br>
<br>
`@`
<br>
*Must* match an __"@"__ symbol.
<br>
<br>
```(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?.)``` `+`
<br>
Match *one or more* of the preceding characters within the defined character sets.
<br>
<br>
```[a-z0-9](?:[a-z0-9-]*[a-z0-9])``` `?`
<br>
Match *zero or one* of the preceding characters within the defined character sets.

---

### Grouping Constructs

A capturing group is defined when the objects of that group are placed inside parenthesis "( )". It allows mini patterns to be created within our larger patterns. For example, if you were trying to find all instances of "the" or "The" in a string you could use a *grouping constructor*.
<br>
The expression would look like this `/(t|T)he/g`.
<br>
Because it is its own group, you can also apply individual quantifiers to that group such as `/(t|T){2,3}he/`

This operator is very useful when we need to extract information from strings or data using your preferred programming language. Any multiple occurrences captured by several groups will be exposed in the form of a classical array: we will access their values specifying using an index on the result of the match. [2]

*Let's look at a snippet from our comprehensive example:*
<br>

```(?:[a-z0-9-]*[a-z0-9])```
<br>

At the beginning of this portion of our RegEx we see:
`(?:` 
<br>
This indicates a *non-capturing group*. It groups multiple tokens together without creating a capture group.

---

### Bracket Expressions: `[ ]`

A bracket expression is either a matching list expression or a non-matching list expression. It consists of one or more expressions: ordinary characters, collating elements, collating symbols, equivalence classes, character classes, or range expressions. [4]

In our example, bracket expressions are used to represent character sets.

`[`
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`a-z` : matches a character in the range of a to z (char codes 97 through 122) and is case sensitive.
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`0-9` : matches a character in the range of 0 to 9 (char codes 48 through 57) and is case sensitive.
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`!` `#` `$` `%` `&` `'` `*` `+` `/` `=` `?` `^` `_` ``` ` ``` `{` `|` `}` `~` `-` : matches any of the characters specified (char codes 33, 35-39, 42-43, 47, 61, 63, 94-96, 123-126, 45 respectively).
<br>
`]`

---

### Character Classes

Character classes are a shorthand way to represent a group of characters.
In our simple email RegEx we are using this with the `\S`. This represents a single character that *is not* white space. Character classes always start with a single backslash `\` which escapes the literal meaning of that character.

Some common examples are:

- `\s` : single whitespace character
- `\S` : single character that is NOT white space
- `\u` : single uppercase character `[A-Z]`
- `\U` : single character that is not uppercase `[^A-Z]`
- `\w` : word character `[a-zA-Z0-9_]`
- `\W` : single character that is NOT a word character `[^a-zA-Z0-9_]`
- `\x00-\xFF` : hexadecimal character
- `\cX` : ASCII control character
- `\d` : single digit `[0-9]`
- `\D` : single character that is NOT a digit `[^0-9]`
- `\E` : stop processing escaped characters
- `\l` : match a single lowercase letter `[a-z]`
- `\L` : single character that is not lowercase `[^a-z]`

[5]

---

### The OR Operator

In RegEx `OR` is represented by a single vertical bar `|`. It enables as to match a collection of text against two different test patterns, if either returns true it becomes a match.

We do not use the `OR` operator in either of our email examples, but here is a quick summary of how it works. [6]

```^I like (dogs|penguins), but not (lions|tigers).$```

This expression will match any of the following strings:

```
I like dogs, but not lions.
I like dogs, but not tigers.
I like penguins, but not lions.
I like penguins, but not tigers.
```

---

### Flags

Flags, in a regular expression, are tokens that modify its behavior of searching. Flags are optional parameters that we can add to a plain expression to make it search in a different way. Each flag is denoted by a single alphabetic character, and serves different purposes in modifying the expression's searching behaviour. [7]

We do not use any flags in either of our email examples, but here is a quick summary of how it works.

```/Hello/i```

This expression will match any of the following strings:

```
hello
HELLO
HeLlo
helLO
```

and so on.

Some common examples are:

- `i` : Ignore Casing - makes the expression search case-insensitively 
- `g` : Global - makes the expression search for all occurences
- `s` : Dot All - makes the wild character `.` match new lines as well
- `m` : Multiline - makes the boundary characters `^` and `$` match the beginning and ending of every single line instead of the beginning and ending of the whole string
- `y` : Sticky - makes the expression start its searching from the index indicated in its `lastIndex` property
- `u` : Unicode - makes the expression assume individual characters as *code points*, not *code units*, and thus match 32-bit characters as well

---

### Character Escapes

The backslash in a regular expression precedes a literal character. You also escape certain letters that represent common character classes, such as `\w` for a word character or `\s` for a space. [8]

Our example doesn't call for the use of character escapes, but here is a quick summary of how it works.

- `\\` : Represents a single backslash character
- `\+` : Represents a single "+" character
- `\A` : Represents the start of a string
- `\d` : represents a single digit `[0-9]`

---

## Author

This article is written by me, Bridget Louise McCavanagh, a Full Stack Web Developer.

---

## Questions

If you have any questions, check out my <a href="https://www.github.com/blmccavanagh">GitHub</a> or email me <a href="mailto:blmccavanagh@gmail.com">here</a>.

---

<div align="center">

**Thank you for visiting.**

</div>

---

### References

[1] https://en.wikipedia.org/wiki/Regular_expression
<br>
[2] https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285
<br>
[3] https://docs.microsoft.com/en-us/dotnet/standard/base-types/quantifiers-in-regular-expressions
<br>
[4] https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap09.html#:~:text=A%20bracket%20expression%20is%20either,character%20classes%2C%20or%20range%20expressions.
<br>
[5] https://javascript.info/regexp-character-classes
<br>
[6] https://www.ocpsoft.org/tutorials/regular-expressions/or-in-regex/
<br>
[7] https://www.codeguage.com/courses/regexp/flags
<br>
[8] https://www.jmp.com/support/help/en/16.0/index.shtml#page/jmp/escaped-characters-in-regular-expressions.shtml