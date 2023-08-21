# How to Interpret a URL Regular Expression

So we have the following regular expression: 

/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/

We know that it's a regular expression, but what on earth does it mean??? Keep reading to find out!

## Summary

Today, I will be going over how to read, take apart and make sense of regular expressions, beginning with the following expression that defines the criteria for a functional URL. 

Regular Expression (Regex): /^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/

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
- [Explanation (Detailed)](#explanation-detailed)

## Regex Components

Regular Expression (Regex): /^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/

Opening Anchor: /^ 
Group 1: (https?:\/\/) 
    Literals: h, t, t, p, s
    Quanitifier: ?, applies only to the s
    Literal: ":"
    Escaped characters: \/\/, will show up as //
Quantifier: ?
Group 1: ([\da-z\.-]+)
    Character set: [\da-z\.-]
        Digit: \d
        Range: a-z. Case sensitive.
        Escaped character: \., will appear as .
        Literal: -
    Quantifier: +
An escaped period: \., will appear as .
Group 2: ([a-z\.]{2,6})
    Character set: [a-z\.]
        Range: a-z
        Escaped character: .
    Quantifier: {2,6}
        Range: 2,6 which means between 2 and 6
Group 3: ([\/\w \.-]*)
    Character set: [\/\w \.-]
        Escaped character: /
        Word character: \w, the equivalent of [A-Za-z0-9_]
        A space: " "
        Escaped character: .
        Literal: -
    Quantifier: *
Quantifier: *
An escaped forward slash: \/
Quantifier: ?
Closing Anchor: $/

### Anchors
/^: Opening
$/: Closing

### Quantifiers
?: 1 or 0
{2,6}: between 2 and 6
*: 0 or more

### OR Operator
none

### Character Classes
h: literal (Case Sensitive)
t: literal (Case Sensitive)
t: literal (Case Sensitive)
p: literal (Case Sensitive)
s: literal (Case Sensitive)

### Flags
none

### Grouping and Capturing
(): Group
[]: character set

### Bracket Expressions
[]: character set

### Greedy and Lazy Match
+: 1 or more
*: 0 or more
?: as few times as possible

### Boundaries
/^ and $/: boundaries of a regular expression
( and ): boundaries of a token group
[ and ]: boundaries of a character set
{ and }: boundaries of a range

### Back-references
none

### Look-ahead and Look-behind
none

### Explanation (Detailed)

The /^ that we see in the very beginning indicates the beginning of the regular expression. The ( following the ^ indicates the opening up of a "group" that captures multiple "tokens" together. The following characters, h, t, t, p and s each inidicate specific characters that will appear as a part of the group. Keep in mind. These characters are case sensitive. The ? that follows is a quantifier, that indicates the preceeding tokens, https will appear either once or 0 times. The : that comes after is treated like the lower case characters. It will simply exist as a token, following the https. The \ that follows, indiciates the "escaping" of the following character, and the / that follows is the character that is "escaped", meaning all semantic meaning has been removed from the /, and it now simply exists in the expression as a /. The same goes for the following \ and the / that comes after. The ) indicates the closing of the first group. 

The "?" that comes after indicates that the previous group can either exist, or not exist, but that there cannot be any multiples. 

We then see the opening up of another group. The "[" that follows indicates the opening up of a character set. The \d after that indicates that the character set may include digits between 0 and 9. The a-z that follows indicates that the character set may contain letters between a-z (case sensitive). The \ that follows escapes the ".", meaning "." may also appear in the character set. The same logic applies for the "-". But the "-" doesn't need to be "escaped". We then see the closing of the character set, and a "+" sign that indicates that the character set may consist of 1 or more tokens. We then see the closing of the second group. 

The \. we see between the 2nd and 3rd group is an escaped "." that's a part of the URL. 

We then see the opening up of yet another group. (3rd). The first thing we see is the opening up of another character set. We then see an a-z, an escaped ".", and the closing of the character set. The {2,6} that follows indicates that the preceeding character set that was just defined may be anywhere between 2 and 6 characters(tokens) long. We then see the closing of the third group.

Without anything in between, we see the opening up of a 4th group, and the opening up of another character set, which introduces an escaped "/", indicating that the character set may contain "/"s, a \w, which is shorthand for word, indicating the inclusion of any word character, (the equivalent of [a-zA-Z0-9_]). The space that follows introduces spaces as elligible tokens of the character set. We then see an escaped "." and a -, both of which are also introduced as elligible tokens. We then see the closing of the character set, followed by a "*", a wildcard, indicating that the preceeding character string can be of any length. 

The "*" that follows indicates that there may be any number of groups that follow the preceeding criteria, or that such groups might not exist at all. We then see an escaped "/", a "?" that indicates the optional nature of the escaped "/", and a "$/" that indicates the end of the regular expression. 

## Author


Justin Choi
email: justinschoi93@gmail.com
github: justinschoi || https://github.com/justinschoi93

## Technologies Used
MDN || https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions
RegExR || https://regexr.com/