# Regex-Tutorial- Matching an Email

In this tutorial, I'm going to be introducing one of the most commonly used regular expressions, by describing it in words and how it works,

##Summary

We will be walking through the follwoing regex, explaining what each component does.

/^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/

This regex makes sure that the given string matches the template for an email address.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors
The two anchors in regex are ^ and $.

^ means that the following code must appear at the beginning of the string.

$ means that the preceding code must appear at the end of the string.

Because our regular expression contains both, a given string must match all the given specifications exactly, or it won't be a match.

Although this sounds limiting, you will see how quantifiers, grouping and bracket expressions allow a large range of variation in the given string.

### Quantifiers
Quantifiers are used to specify how many times a given character is expected to appear.

Our regex uses two quantifiers, + and {2,6}.

In our expression, [a-z0-9_.-]+ means that any character matching the characters inside the brackets is expected to appear at least once, with no upper limit.

The same is true of [\da-z.-]+

[a-z.]{2,6} means that 2 to 6 characters matching those inside the brackets are expected. The numbers inside the curly braces specify the lower and upper limit of the number of characters expected.


### Grouping Constructs
Grouping and capturing is done with ( ) in regex.

Anything within a set of parentheses is taken as a single group, which allows all the information inside to be treated as a single unit.

Look at the entire expression, paying special attention to the parentheses.

/^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/

Between /^ and $/, there are three distinct character groups, ([a-z0-9_.-]+), ([\da-z.-]+), and ([a-z.]{2,6}).

If we remove the internal logic, the regex can be expressed this way: (1)@(2).(3). This is much easier to read, and corresponds to what we know about email addresses, which always follow the (string)@(website).(com/edu/etc) template.



### Bracket Expressions
The final piece necessary to our RegEx is bracket expressions. There are three within our code:

[a-z0-9_.-], [\da-z.-], and [a-z.]

A bracket expression represents a single character. The character can be anything specified within the brackets. So, for example, in [a-z0-9_.-], this character will be matched by any lowercase letters from a-z, any digit from 0-9, or a period.

Combined with the quantifier +, this piece of code means that any number of characters matching those specified within the brackets will match.

### Character Classes
Regex has special character classes that match types of characters.

In our expression, \d is used to match any digit character.

The backslash is necessary in order to differentiate the digit class from a plain letter d.

Although we only have one character class in the expression, the behavior-changing function of a backslash is helpful in understanding another frequently used part of the expression, ".".

Unlike the other character classes, \d, \w (matching a word character) and \s (matching a whitespace character), the character class ".", which matches any character, does not require a backslash.

Because of the unique behavior of ".", the backslash must be used to negate its use as a character class and interpret it as the character ".".

### The OR Operator
| and []

x(y|z) matches a string that has x followed by y or z; captures y and z, this will be explained later xy or xz but not xyz

x[yz] same as above but it does not capture y or z xy or xz but not xyz

### Flags
g m and i

Flags are added after the search pattern as been delimited by two slash characters / g - global

/xyz/g for example will continue to search after the first match, starting from the end of the previous match

m - multiline; is combined with ^ and & to match the start and end of a line respectively, not the whole string

i - insensitive; makes an expression case-insistive

/xyz/i would match XYZ where as /xyz/ would only match xyz

### Character Escapes
Character escapes are to be taken literally. For example, in our matching an email regex: 
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
We can see that there are 5 separate character escapes. 

They are:
   - \.
   - \d
   - \.
   - \.
   - \.

The backslash ( \ ) in all of the ( \. )  is meant to tell the regex to take the (.) literally and search for that as one of the characters in the email addresses. It is aknowledging that email addresses can contain periods (.) in the naming part of the email (for example: maltopia23@outlook.com is a valid email that would be picked up by the regex because the period os quite literally there in the name.)

The same goes for where ( \. ) is found in the rest of the regex, it can, quite literally, contain a period (.). 

The ( \d ) character escape represents any number 0-9

## Author
Malcolm Hendrix
https://github.com/Malcolm0729
