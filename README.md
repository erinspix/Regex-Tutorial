# Title Regex-Gist

Regular expressions, often referred to as regex, are sequences of characters used to define search patterns within text. Regex is a powerful tool commonly used for input validation, pattern matching, and string manipulation. In this tutorial, we will explain the components of a regular expression used to validate email addresses and show how each part works to ensure the input follows the correct format.


## Summary

We will be analyzing the following regular expression, which is designed to verify that user input follows the format of a valid email address:

regex

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

This regex checks for:

A username containing valid characters before the "@" symbol.
A domain name following the "@".
A top-level domain after a period (such as .com, .org, or .net), which has a length between 2 and 6 characters.

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
Anchors are special metacharacters that mark the beginning or end of a string. They help determine where a pattern should start and end:

^ (Caret): Matches the start of the string.
$ (Dollar sign): Matches the end of the string.
In the email validation regex, these anchors ensure that the entire input is validated as an email address, not just a portion of it.
^: The caret (^) matches the start of the string.
$: The dollar sign ($) matches the end of the string.
These anchors ensure that the entire input is validated as an email address, not just part of it.

### Anchors
Quantifiers:
Quantifiers specify the number of occurrences of a character or group. They define how many instances of a character or set of characters must be present for a match:

+: The plus sign (+) is a greedy quantifier that matches one or more of the preceding element. For example, ([a-z0-9_\.-]+) allows for one or more characters in the username.
{2,6}: This quantifier specifies a range, ensuring that the top-level domain (like .com) has between 2 and 6 characters.

### Quantifiers
Quantifiers:
Quantifiers specify the number of occurrences of a character or group. They define how many instances must be present for a match:

+ (Plus sign): A greedy quantifier that matches one or more of the preceding element. In the email regex, ([a-z0-9_.-]+) allows for one or more characters in the username.
{2,6}: Specifies a range, ensuring that the top-level domain (like .com) has between 2 and 6 characters.

### OR Operator
The OR operator (|) allows for matching between multiple alternatives. While it is not used in this specific email validation regex, it is a common component in regex patterns for defining multiple possible matches.

For example, the pattern a|b would match either "a" or "b" in a given string.
### Character Classes
Character Classes:
Character classes allow for defining sets of characters that can be matched within a string. In the email validation regex, the following character classes are used:

\d: Matches any digit from 0 to 9.
[a-z]: Matches any lowercase letter from 'a' to 'z'.
[_.-]: Matches literal underscore, period, and hyphen characters.
These character classes define which characters are allowed at specific positions within the email string, ensuring that the input follows the correct format.
### Flags
Flags:
Flags modify how a regex is applied, controlling certain features like case sensitivity and whether the search should continue after the first match:

g (Global flag): Searches for all possible matches in a string, not just the first one.
i (Ignore case flag): Makes the search case-insensitive, allowing matches regardless of letter casing.
In this email validation regex, no flags are used, as the input is expected to be fully lowercase.
### Grouping and Capturing
Grouping constructs are used to group parts of a regex, treating multiple characters as a single unit. Parentheses (()) are used for capturing, meaning they store parts of the matched string for potential future reference. In the email validation regex, the following groups are present:

([a-z0-9_.-]+): Captures the username part of the email, which appears before the "@" symbol.
([\da-z.-]+): Captures the domain name after the "@" symbol.
([a-z.]{2,6}): Captures the top-level domain (e.g., ".com") after the period.
These groups ensure that the complete structure of an email address is captured and validated accurately.

### Bracket Expressions
Bracket Expressions:
Bracket expressions, denoted by [], are used to match any one character from a defined set. They specify which characters are allowed at specific positions within a string:

[a-z0-9_.-]: Matches lowercase letters (a-z), digits (0-9), underscores (_), periods (.), and hyphens (-).
[\da-z.-]: Matches digits (\d), lowercase letters (a-z), periods (.), and hyphens (-).
These expressions ensure that only valid characters are included at specific parts of the email address.
### Greedy and Lazy Match
Regex quantifiers can be either greedy or lazy:

Greedy quantifiers try to match as much of the string as possible. In the email validation regex, the + quantifier is greedy, meaning it will match as many characters as possible before moving on to the next part of the pattern.
Lazy quantifiers, on the other hand, try to match as little as possible. To make a quantifier lazy, add a ? after it (e.g., +?).
In this regex, the greedy behavior of + is used to ensure that the username and domain parts of the email capture as many valid characters as possible.
### Boundaries
The boundaries of this regex are defined by the ^ and $ anchors, which ensure that the match is for the entire string. In the email validation regex, these anchors guarantee that the input will only match if it forms a complete and valid email address, not just a partial match within a larger string.
### Back-references
Back-references: Back-references in regular expressions allow you to refer to previously captured groups and reuse their values later in the pattern. They are denoted by a backslash () followed by the number of the capture group they refer to. For example, \1 refers to the first captured group, \2 to the second, and so on.

example: <(h1)>(.*?)</\1>

The first part (h1) captures the tag name. \1 refers to the first capture group (which contains h1), ensuring that the closing tag matches the opening tag. In the case of the email validation regex you provided, there are no back-references being used, as the structure of an email doesn't require referring back to previously captured groups.
### Look-ahead and Look-behind

ook-ahead and Look-behind:
Look-ahead and look-behind are known as zero-width assertions in regular expressions. They allow you to assert that a certain condition exists either ahead of or behind the current position in the string, without actually consuming any characters from the string. This means that they check for a condition without including it in the match.

Look-ahead (positive and negative):
Positive look-ahead ((?=...)) ensures that what follows the current position matches a specific pattern.
Negative look-ahead ((?!...)) ensures that what follows does not match a specific pattern.
Example of positive look-ahead:
\w+(?=@example.com)
This matches any word (\w+) that is followed by @example.com, but it does not include @example.com in the match itself.

Example of negetive look-ahead:
\b\w+\b(?!@gmail.com)

This matches any word that is not followed by @gmail.com.
Look-behind (positive and negative):
Positive look-behind ((?<=...)) ensures that what precedes the current position matches a specific pattern.
Negative look-behind ((?<!...)) ensures that what precedes does not match a specific pattern.
Example of positive look-behind:

(?<=@)\w+

This matches a word that is preceded by an @ symbol, but the @ itself is not included in the match.
Example of negative look-behind:
(?<!@)\w+

-This matches a word that is not preceded by an @ symbol.
In the email validation regex:
The email validation regex does not use look-ahead or look-behind assertions, since the structure of an email is fairly straightforward and doesn't require conditional checks ahead or behind specific characters.

## Author
Erin Spix is a web development student and art lead for a California-based startup. She lives in michigan with her old dog and two fluffy chinchillas.  You can find more of her work on GitHub.
https://github.com/erinspix
