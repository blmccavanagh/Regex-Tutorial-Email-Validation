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

---

### Anchors: `^` `&` `$`
<br>
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
<br>
Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found. [3]
<br>
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
__Match one or more of any character__
<br>
`@` `+`
<br>
__Match an "@" symbol.__
<br>
`\S` `+`
<br>
__Match one or more of any character.__
<br>
`\.` `+`
<br>
__Match an "." symbol.__
<br>
`\S`
<br>
__Match one or more of any character__

*Now lets look at the comprehensive example:*

```/[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*@(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?/g```

This means:
<br>
<br>
```[a-z0-9!#$%&'*+/=?^_`{|}~-]```
<br>`+`
<br>
Match one or more of the preceding characters.
<br>
<br>
```(?:.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)```
<br>
`*`
<br>
Match zero or more of the preceding characters.
<br>
<br>
`@`
<br>
An __"@"__ symbol.
<br>
<br>
```(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?.)```
<br>
`+`
<br>
Match one or more of the preceding characters.
<br>
<br>
```[a-z0-9](?:[a-z0-9-]*[a-z0-9])```
<br>
`?`
<br>
Match zero or one of the preceding characters.

---

### Grouping Constructs

A capturing group is defined when the objects of that group are placed inside parenthesis "( )". It allows mini patterns to be created within our larger patterns. For example, if you were trying to find all instances of "the" or "The" in a string you could use a *grouping constructor*.
<br>
The expression would look like this `/(t|T)he/g`.
<br>
Because it is its own group, you can also apply individual quantifiers to that group such as `/(t|T){2,3}he/`

This operator is very useful when we need to extract information from strings or data using your preferred programming language. Any multiple occurrences captured by several groups will be exposed in the form of a classical array: we will access their values specifying using an index on the result of the match. [2]

*Let's look at the comprehensive example:*
<br>
<br>
`(?:` 
<br>
This indicates a *non-capturing group*. It groups multiple tokens together without creating a capture group.

---

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
<br>
[3] https://docs.microsoft.com/en-us/dotnet/standard/base-types/quantifiers-in-regular-expressions