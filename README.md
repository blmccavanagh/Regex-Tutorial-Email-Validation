# RegEx Tutorial - Email Validation

## This GitHub repository contains a tutorial explaining the use of regular expressions in coding.

## Summary

A regular expression, typically referred to as RegEx or RegExp, is a sequence of characters that specifies a search pattern. Usually such patterns are used by string-searching algorithms for "find" or "find and replace" operations on strings, or for input validation. It is a technique developed in theoretical computer science and formal language theory. [1]

This tutorial will show you how to build a RegEx that checks wether an email address is valid or not.

## Example

A simple example of a RegEx to validate an email input is:

```/\S+@\S+\.\S+/```

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

---

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

### Quantifiers: `+` `?` and `{}`

---

### Grouping Constructs

### Bracket Expressions

### Character Classes

### The OR Operator

### Flags

### Character Escapes

## Author

This article is written by me, Bridget Louise McCavanagh, a Full Stack Web Developer.

### References

[1] https://en.wikipedia.org/wiki/Regular_expression
<br>
[2] https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285