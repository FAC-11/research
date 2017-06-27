What are Regular Expressions?
=============================

A regular expression is a pattern describing a certain amount of text, most commonly used for matching and replacing. You will usually find the name abbreviated to "regex" or "regexp".

The most basic regular expression consists of a single literal character, such as a. It matches the first occurrence of that character in the string. If the string is Jack is a boy, it matches the a after the J. The fact that this a is in the middle of the word does not matter to the regex engine.

Note that regex engines are case sensitive by default. cat does not match Cat, unless you tell the regex engine to ignore differences in case.

To write a simple pattern simply put the text between two forward slashes.

Use special characters when you want more than a direct match, such as finding multiple letter 'b's or finding white space.

Special Characters
------------------

Because we often want to do more than simply search for literal pieces of text, we need to reserve certain characters for special use. These special characters are often called "metacharacters". Most of them are errors when used alone.

If you want to use any of these characters as a literal in a regex, you need to escape them with a backslash.

 - \ A backslash before a non-special character indicates the next character is special, and vice versa.
 - . Matches any character, except for line breaks if dotall is false.
 - \* Matches 0 or more of the preceding character. For example, /bo*/ matches 'boooo' in "A ghost booooed"
 - \+ Matches 1 or more of the preceding character. For example, /a+/ matches the 'a' in "candy" and all the a's in "caaaaaaandy", but nothing in "cndy".
 - ? Preceding character is optional. Matches 0 or 1 occurrence.
 - \d Matches any single digit
 - \w Matches any word character (alphanumeric & underscore).
 - [XYZ] Matches any single character from the character class.
 - [XYZ]+ Matches one or more of any of the characters in the set.
 - \$ Matches the end of the string. For example, /t$/ does not match the 't' in "eater", but does match it in "eat".
 - ^ Matches the beginning of a string. For example, /^A/ does not match the 'A' in "an A", but does match the 'A' in "An E".
 - [^a-z] When inside of a character class, the ^ means NOT; in this case, match anything that is NOT a lowercase letter.
 
A useful tool for creating regular expressions is [regex101](https://regex101.com).
It also has a library with already published regular expressions from other users -anyone can make an account and contribute his own code as well as vote up or down on.
Other resources:
[regexpr](http://regexr.com/)
[regextester](http://www.regextester.com/)
