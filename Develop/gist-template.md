# Title (replace with your title)

Introductory paragraph (replace this with your text)

## Summary

Regular expressions (regex) can be used to match email addresses. There are different patterns for matching email addresses, depending on the level of specificity needed. A simple pattern checks for the presence of an "@" symbol and a period (".") symbol, and a minimum length of 3 characters. A more complex pattern matches a wider range of valid email addresses, including those with subdomains and special characters. The most comprehensive and strict pattern is based on the email address specification in RFC 5322 and includes rules for validating the format of email addresses. No regex pattern can match all possible email addresses, as there are many variations and formats that are technically valid. These patterns can be adjusted or combined with other rules depending on your specific use case.

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
[Character classes] "\w":
In an email address regex, you can use character classes to match specific characters or groups of characters. For example, the character class "\w" matches any word character (letters, digits, and underscores).

[Quantifiers] "@":
In an email address regex, you can use quantifiers to match a certain number of characters before or after the "@" symbol. For example, the quantifier "+" matches one or more occurrences of the preceding character or group, and is often used to match one or more characters before the "@" symbol.

[Alternation] "(com|org|net)":
In an email address regex, you can use alternation to match different TLDs (top-level domains) or to match different subdomains. For example, the pattern "(com|org|net)" matches the TLDs .com, .org, or .net.

[Escaping special characters] "." or "+":
In an email address regex, you may need to escape special characters such as "." or "+". For example, the pattern "." matches a literal period character instead of any character.

[Grouping]  "([a-zA-Z0-9.-]+.[a-zA-Z]{2,})":
In an email address regex, you can use grouping to group together certain parts of the email address, such as the domain or the TLD. For example, the pattern "([a-zA-Z0-9.-]+.[a-zA-Z]{2,})" groups together the domain and TLD as a single subexpression.

### Anchors
[Beginning of line anchor] (^):
the regex pattern "^[\w.%+-]+@[a-zA-Z0-9.-]+.[a-zA-Z]{2,}$" would match an email address that starts at the beginning of a line and ends at the end of a line.

[End of line anchor] ($):
the regex pattern "^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+.[a-zA-Z]{2,}$" would match an email address that starts at any position in a string and ends at the end of a line.

[Word boundary anchor] (\b):
the regex pattern "\b[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+.[a-zA-Z]{2,}\b" would match an email address that is not part of a larger word or phrase.

### Quantifiers
"+" (one or more):
In an email address regex, the plus symbol can be used to match one or more characters before the "@" symbol, such as in the pattern "\w+@[a-zA-Z0-9.-]+.[a-zA-Z]{2,}" which matches an email address with one or more word characters before the "@" symbol.

"" (zero or more):
In an email address regex, the asterisk symbol can be used to match zero or more characters before the "@" symbol, such as in the pattern "[a-zA-Z0-9._%+-]@[a-zA-Z0-9.-]+.[a-zA-Z]{2,}" which matches an email address with zero or more alphanumeric characters, dots, underscores, percent signs, plus signs or hyphens before the "@" symbol.

"?" (zero or one):
In an email address regex, the question mark symbol can be used to match an optional character or group, such as in the pattern "[a-zA-Z0-9._%+-]?@[a-zA-Z0-9.-]+.[a-zA-Z]{2,}" which matches an email address with zero or one alphanumeric characters, dots, underscores, percent signs, plus signs or hyphens before the "@" symbol.

"{n}" (exactly n):
In an email address regex, this can be used to match a specific number of characters before or after the "@" symbol. For example, the pattern "\w{4}@[a-zA-Z0-9.-]+.[a-zA-Z]{2,}" would match an email address with exactly 4 word characters before the "@" symbol.

"{n,}" (n or more):
In an email address regex, this can be used to match a minimum number of characters before or after the "@" symbol. For example, the pattern "\w{3,}@[a-zA-Z0-9.-]+.[a-zA-Z]{2,}" would match an email address with at least 3 word characters before the "@" symbol.

"{n,m}" (between n and m):
In an email address regex, this can be used to match a specific range of characters before or after the "@" symbol. For example, the pattern "\w{2,5}@[a-zA-Z0-9.-]+.[a-zA-Z]{2,}" would match an email address with between 2 and 5 word characters before the "@" symbol.

### OR Operator
The OR operator in regex is denoted by the pipe symbol |.

\w+@[a-zA-Z0-9.-]+(com|org|net)
In this regex pattern, the | operator is used to match any one of the TLDs com, org, or net. The rest of the pattern matches one or more word characters before the "@" symbol, followed by one or more characters in the domain name, which can include letters, digits, periods, and hyphens.

\w+@(sales|support)\.[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}
In this pattern, the | operator is used to match either sales or support as the subdomain, followed by the domain name and TLD.

### Character Classes
[a-zA-Z]: matches any uppercase or lowercase letter. This character class is commonly used to match the domain name or the username part of an email address.

[0-9]: matches any digit. This character class can be used to match the domain name or username part of an email address that contains digits.

[\w.-]: matches any word character, period or hyphen. This character class can be used to match the domain name part of an email address, which can include periods and hyphens.

[\s\S]: matches any character, including newlines. This character class can be used to match any part of an email address, including the body of the email.

[^a-zA-Z0-9]: matches any character that is not an uppercase or lowercase letter or a digit. This character class can be used to match any special characters that might be included in an email address, such as !, #, $, %, &, *, +, -, /, =, ?, ^, _, {, |, }, or ~.

[\w.-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}
In this pattern, the first character class [\w.-] matches one or more word characters, periods, or hyphens before the "@" symbol. The second character class [a-zA-Z0-9.-] matches one or more letters, digits, periods, or hyphens in the domain name. The final character class [a-zA-Z]{2,} matches the TLD, which must consist of at least two letters.

### Flags
g: the global flag, which allows the pattern to match multiple times within a string. This flag is often used in conjunction with other flags to match all occurrences of a pattern.

i: the case-insensitive flag, which allows the pattern to match both uppercase and lowercase letters. This flag is useful for matching email addresses, which can contain uppercase or lowercase letters in the domain name and username.

m: the multi-line flag, which changes the behavior of the ^ and $ anchors so that they match the beginning and end of each line in a multi-line string. This flag is useful when you are matching email addresses that might appear on separate lines within a text file.

s: the dot-all flag, which allows the dot . character to match any character, including newlines. This flag is useful when you are matching the body of an email, which might contain newlines.

u: the unicode flag, which enables full Unicode support in the pattern. This flag is useful when you are matching email addresses that might contain non-ASCII characters, such as accented letters.

/\b[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}\b/i
In this pattern, the i flag is included at the end of the pattern to indicate that the pattern should match both uppercase and lowercase letters in the domain name and username. This makes the pattern more flexible and able to match a wider range of email addresses.

### Grouping and Capturing
/(\b[\w.%+-]+)@([\w.-]+)\.([A-Z]{2,})\b/i

The first group (\b[\w.%+-]+) captures the username, which can consist of one or more word characters, periods, hyphens, or special characters such as percent signs, plus signs, or hyphens.

The second group ([\w.-]+) captures the domain name, which can consist of one or more word characters, periods, or hyphens.

The final group ([A-Z]{2,}) captures the TLD, which must consist of at least two uppercase letters.

Once the pattern has been matched against a string, you can use the match() method to extract the captured groups from the match object. Here is an example of how this might be done in JavaScript:

const email = "jane.doe@example.com";
const pattern = /(\b[\w.%+-]+)@([\w.-]+)\.([A-Z]{2,})\b/i;
const match = email.match(pattern);

console.log(match[1]); // "jane.doe"
console.log(match[2]); // "example"
console.log(match[3]); // "com"

### Bracket Expressions
To match letters, digits, and a few special characters that are commonly used in usernames: /[\w.%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}/i

In this pattern, the \w shorthand character class matches any word character (letters, digits, and underscores), and the .%+- characters match the additional special characters that are allowed in usernames.

To match letters, digits, and hyphens that are commonly used in domain names: 
/[\w.-]+@[A-Z0-9.-]+\.[A-Z]{2,}/i

In this pattern, the \w shorthand character class matches any word character, and the .- characters match the hyphens and periods that are allowed in domain names.

To match two or three uppercase letters that are commonly used in TLDs: 
/[\w.-]+@[A-Z0-9.-]+\.[A-Z]{2,3}/i

In this pattern, the bracket expression [A-Z]{2,3} matches two or three uppercase letters that are commonly used in TLDs, such as com, net, or edu.
### Greedy and Lazy Match
([\w.-]+)@([\w.-]+)\.([\w.-]+)

([\w.-]+) matches one or more word characters, dots (.), and hyphens (-), and captures them as a group.

@ matches the @ symbol.

([\w.-]+) matches one or more word characters, dots (.), and hyphens (-), and captures them as a group.

\. matches a literal period (.) character.

([\w.-]+) matches one or more word characters, dots (.), and hyphens (-), and captures them as a group.

Greedy quantifiers are denoted by the + symbol, and they match as much as possible. In this case, the + quantifiers after each of the capture groups will match as many characters as possible, as long as the overall match succeeds. This means that the regex will try to match as much of the email address as it can before backtracking to ensure that the match succeeds. For example, if the email address is john.doe@example.com, the first [\w.-]+ group will match john.doe and the second [\w.-]+ group will match example, leaving com for the last [\w.-]+ group.

Lazy quantifiers are denoted by the +? symbol, and they match as little as possible. In this case, adding a ? after each + quantifier will make them lazy, so that they match as few characters as possible, while still allowing the overall match to succeed. This means that the regex will match the smallest possible portion of the email address before moving on to the next part. For example, if the email address is john.doe@example.com, the first [\w.-]+? group will match john, the second [\w.-]+? group will match doe, and the third [\w.-]+? group will match example.

### Boundaries
\b[\w.-]+@[\w.-]+\.[\w.-]+\b

\b[\w.-]+ matches one or more word characters, dots (.), and hyphens (-), and ensures that this match starts at a word boundary. This means that the match will not start in the middle of a word, such as in the middle of an email address that is part of a larger string of text.

@[\w.-]+\. matches the @ symbol, followed by one or more word characters, dots (.), and hyphens (-), and a literal period (.), and ensures that this match ends at a word boundary. This means that the match will not include any characters that are not part of the domain name, such as whitespace or punctuation that might appear after the domain name.

[\w.-]+\b matches one or more word characters, dots (.), and hyphens (-), and ensures that this match ends at a word boundary. This means that the match will not include any characters that are not part of the domain name, such as additional letters or punctuation that might appear after the domain name.

### Back-references
\b(\w[-.\w]*\w)@(\w[-.\w]*\w)\.(\w{2,3})\b

\b matches a word boundary, ensuring that the regular expression starts at the beginning of a word.

(\w[-.\w]*\w) captures the "username" of the email address. This can consist of one or more word characters, followed by zero or more hyphens, dots, or word characters, and ending with a word character.

@ matches the "@" symbol, which separates the "username" from the "domain name".
(\w[-.\w]*\w) captures the "domain name" of the email address. This can consist of one or more word characters, followed by zero or more hyphens, dots, or word characters, and ending with a word character.

\. matches a literal period, which separates the "domain name" from the top-level domain.

(\w{2,3}) captures the top-level domain, which consists of two or three word characters (such as "com" or "edu").

\b matches a word boundary, ensuring that the regular expression ends at the end of a word.

### Look-ahead and Look-behind
(?<=\s|^)[\w.+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}(?=\s|$)

(?<=\s|^) is a positive lookbehind that matches a whitespace character or the start of the string. This ensures that the regular expression is preceded by a space or the beginning of the string, but does not include the space or string in the match.

[\w.+-]+ matches one or more word characters, dots (.), plus signs (+), and hyphens (-), which can appear in the "username" of the email address.

@ matches the "@" symbol, which separates the "username" from the "domain name".

[A-Za-z0-9.-]+ matches one or more letters, digits, dots (.), hyphens (-), and the at symbol (@), which can appear in the "domain name" of the email address.

\. matches a literal period, which separates the "domain name" from the top-level domain.

[A-Za-z]{2,} matches two or more letters, which make up the top-level domain (such as "com" or "edu").

(?=\s|$) is a positive lookahead that matches a whitespace character or the end of the string. This ensures that the regular expression is followed by a space or the end of the string, but does not include the space or string in the match.

## Author

<https://github.com/jackiezheng1998>
