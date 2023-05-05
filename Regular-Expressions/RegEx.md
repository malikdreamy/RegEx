RegEx /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Regex, short for Regular Expression, is a sequence of characters that define a search pattern. It is a powerful tool used to manipulate and analyze text data. Regular expressions can be used to search, replace, and match text based on specific patterns or rules. Regex can be used in various programming languages. Regex is especially popuar in JavaScript. In Javascript RegEx are used to perform complex operations such as searching for patterns in text, extracting specific parts of text and validating input data.

In this tutorial, I will be going over the popular Regex pattern 
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ which is very useful for validating email addresses.
^ - this is the start of the string anchor, which means the pattern will match at the beginning of the string.
([a-z0-9_\.-]+) - this is a capturing group that matches one or more of the characters inside the brackets: lowercase letters (a-z), digits (0-9), underscore (_), period (.), and hyphen (-). This group captures the username part of the email address.
@ - this matches the "@" symbol in the email address.
([\da-z\.-]+) - this is another capturing group that matches one or more of the characters inside the brackets: digits (\d), lowercase letters (a-z), period (.), and hyphen (-). This group captures the domain name part of the email address.
\. - this matches the "." in the domain name.
([a-z\.]{2,6}) - this is the final capturing group that matches two to six lowercase letters or periods. This group captures the top-level domain part of the email address.
$ - this is the end of the string anchor, which means the pattern will match at the end of the string.
So, putting it all together, this regular expression matches an email address with the format "username@domain.com", where the username can contain lowercase letters, digits, underscore, period, and hyphen, and the domain name can contain digits, lowercase letters, period, and hyphen, and the top-level domain can contain two to six lowercase letters or periods.

# Table of Contents

- <a href="#Anchors">Anchors</a>

- <a href="#Quantifiers">Quantifiers</a>

- <a href="#OR-Operator">OR Operator</a>

- <a href="#Character-Classes">Character-Classes</a>

- <a href="#Flags">Flags</a>

- <a href="#Grouping-and-Capturing">Grouping and Capturing</a>

- <a href="#Bracket-Expressions">Bracket-Expressions</a>

- <a href="#Greedy-and-Lazy-Match">Greedy-and-Lazy-Match</a>

- <a href="#Boundaries">Boundaries</a>

- <a href="#Back-references">Back-references</a>

- <a href="#Look-ahead-and-Look-behind">Look-ahead and Look-behind</a>


<a id="Anchors">Anchors</a>

Anchors in regex are characters that represent a specific position in the input string, rather than a specific character or sequence of characters. Anchors are used to match patterns at specific positions in the input string, such as the beginning or end of the string.
The caret ^ is used as an "anchor" to match the beginning and end of a string.
The dollar sign ($) represents the end of a string. When used in a regex pattern, it matches the end of a line or string
var pattern = /^Hello world!/;
console.log(pattern.test("Hello world!")); // true
console.log(pattern.test("Hello world! 123")); // true
console.log(pattern.test("123 Hello world!")); // false
In this example, ^ is used at the beginning of the pattern to match only strings that start with "Hello world!
If you want to match the word "world" only if it appears at the end of a string, you can use the dollar sign as follows:
const str = "Hello world!";
const pattern = /world$/;
const result = pattern.test(str);
console.log(result); // true

<a id="Quantifiers">Quantifiers</a>

Quantifiers are used to specify the number of times a character or a group of characters should be matched. There are several types of quantifiers in regex:
"*" - matches zero or more occurrences of the preceding character or group.
"+" - matches one or more occurrences of the preceding character or group.
"?" - matches zero or one occurrence of the preceding character or group.
"{n}" - matches exactly n occurrences of the preceding character or group.
"{n,}" - matches n or more occurrences of the preceding character or group.
"{n,m}" - matches between n and m occurrences of the preceding character or group.
Here's an example that uses the + quantifier to match one or more occurrences of the letter 'a':
const str = "banana";
const pattern = /a+/;
const result = pattern.test(str);
console.log(result); // true
The + quantifier is used to match one or more occurrences of the letter 'a'. So, the regex pattern /a+/ will match any string that has one or more 'a' characters in a row. In the given string, "banana" has two 'a' characters in a row, so the test() method returns true.

<a id="OR-operator">OR operator</a>

The | (pipe) symbol is used as the "or" operator, which means it matches either the expression on its left or the expression on its right.
For example, the regular expression /cat|dog/ matches either the string "cat" or the string "dog".
const str1 = "cat";
const str2 = "dog";
const str3 = "bird";
const pattern = /cat|dog/;
console.log(pattern.test(str1)); // true
console.log(pattern.test(str2)); // true
console.log(pattern.test(str3)); // false
The | symbol separates the two options that can match the pattern, and either one can be a valid match.

<a id="Character-Classes">Character Classes</a>

A character class is a way to match a single character from a set of characters. Character classes are in square brackets [] and match any single character within the brackets.
Some examples are:
[aeiou]: matches any vowel character ("a", "e", "i", "o", or "u")
[0-9]: matches any digit character ("0" to "9")
[a-z]: matches any lowercase letter character ("a" to "z")
[A-Z]: matches any uppercase letter character ("A" to "Z")
[A-Za-z0-9]: matches any alphanumeric character ("A" to "Z", "a" to "z", or "0" to "9")
const str = "The quick brown fox jumps over the lazy dog.";
const pattern = /[aeiou]/g;
const matches = str.match(pattern);
console.log(matches); // ["e", "u", "i", "o", "o", "u", "o", "e", "a", "o"]
It is worth noting that we are using the global flag g to return all the charachters. Otherwise if we removed the flag and just used /[aeiou]/; it would only return ["e"] which is the first character match in the string.

<a id="Flags">Flags</a>

flags are optional parameters that modify how the regular expression behaves when it matches a string. They are indicated by a letter immediately following the closing slash of the regular expression.
g (global): matches all occurrences of the pattern, not just the first one.
i (case-insensitive): makes the pattern match case-insensitively, so that uppercase and lowercase letters are treated as equals.
m (multiline): makes the pattern match across multiple lines of text, so that the ^ and $ anchors match at the beginning and end of each line.
const str = "hello world hello";
const pattern = /hello/g;
const matches = str.match(pattern);
console.log(matches); // ["hello", "hello"]
In this example, the regular expression /hello/g matches the string "hello" twice, but because we included the g flag, the match() method returns an array with both matches.

<a id="Grouping-and-Capturing">Grouping and Capturing</a>

Grouping refers to the ability to group together multiple characters in a regular expression. This is done using parentheses. For example, the regular expression (cat|dog) matches either "cat" or "dog", because the pattern is enclosed in a group separated by the | (or) operator.
Capturing refers to the ability to extract or "capture" a portion of the matched text from a regular expression. This is done by enclosing the subpattern to be captured in parentheses. For example, the regular expression /(Hello), (world)!/ captures the words "Hello" and "world" in two separate capturing groups.
const str = "The quick brown fox jumps over the lazy dog";
const pattern = /(fox|dog)/g;
const matches = str.match(pattern);
console.log(matches); // ["fox", "dog"]


<a id="Bracket-Expression">Bracket Expression</a>

Bracket expressions also known as character classes, are a way to match any single character from a specific set of characters in a regular expression.
For example, the regular expression [abc] matches any single character that is either "a", "b", or "c". Similarly, the regular expression [0-9] matches any single digit from 0 to 9.

<a id="Greedy-and-Lazy-Loading">Greedy and Lazy Loading</a>

Greedy and lazy matching are two concepts in regular expressions that describe how patterns match text.
Greedy matching means that a pattern will match as much of the string as possible while still allowing the overall pattern to match. For example, the regular expression .* matches any sequence of characters, as many as possible, until the string or until the next part of the pattern matches.
Lazy matching, on the other hand, matches as little as possible while still allowing the overall pattern to match. It is accomplished by adding a ? after a quantifier such as * or +. For example, the regular expression .*? matches any sequence of characters, as few as possible, until the next part of the pattern matches.
let str = "abbcbbc";
let greedyPattern = /a.*c/;
let lazyPattern = /a.*?c/;

console.log(str.match(greedyPattern)); // ["abbcbbc"]
console.log(str.match(lazyPattern)); // ["abbc"]
In this example, the input string is "abbcbbc". The greedy pattern /a.*c/ matches the longest possible sequence of characters that starts with "a" and ends with "c". Therefore, the match result is ["abbcbbc"].

However, the lazy pattern /a.*?c/ matches the shortest possible sequence of characters that starts with "a" and ends with "c". In this case, that sequence is "ab", because the .*? quantifier is lazy and matches as few characters as possible. Therefore, the match result is ["abbc"].

<a id="Boundaries">Boundaries</a>

Boundaries in regular expressions are used to define specific positions in a string, such as the beginning or end of a line, word, or sentence. Boundaries can be used to specify where a match should start or end, or to ensure that certain characters or sequences are not part of a match.
Here are common boundary symbols used in regular expressions:

^: Matches the beginning of a string or line.
$: Matches the end of a string or line.
\b: Matches a word boundary, which is the position between a word character (as defined by the \w character class) and a non-word character (as defined by the \W character class).
\B: Matches a non-word boundary, which is the position between two word characters or two non-word characters.
Here are some examples of using boundary symbols in regular expressions:
^hello: Matches any string that starts with "hello".
world$: Matches any string that ends with "world".
\bthe\b: Matches the word "the" only if it appears as a separate word, and not as part of another word for example ("theater" or "theme").
\Bee\B: Matches the string "ee" only if it is not surrounded by word characters for example ("seen" or "beef").

<a id="Back-References">Back References</a>

Back-references in regex allow you to refer to a previously matched group in your pattern.
Suppose you have a string that contains two repeated words separated by a space, like this: "hello hello". You can use a regular expression with a back-reference to match this pattern:
/(\w+)\s\1/
In this pattern, (\w+) is a capturing group that matches one or more word characters. The parentheses capture the matched word into a group. The \s matches a whitespace character, and the \1 back-reference matches whatever was captured by the first group, i.e., the repeated word.
So, when you apply this regular expression to the string "hello hello", it will match the entire string. But if you apply it to the string "hello world", it won't match anything, because there are no repeated words.

<a id="Look-ahead-and-Look-behind">Look-ahead and Look-behind</a>

Look-ahead and look-behind in regex are used to match a pattern based on the presence or absence of another pattern before or after it, without including the additional pattern in the match.
For example, suppose you have a string of text that contains a series of email addresses, and you want to extract only the domain names (the part after the @ symbol) but without including the @ symbol itself. You can use a look-behind assertion to match the @ symbol without including it in the actual match: /(?<=@)\w+\.\w+/g
In this pattern, (?<=@) is the positive look-behind assertion that matches the @ symbol preceding the domain name, but doesn't include it in the match. The \w+\.\w+ matches the domain name itself, which consists of one or more word characters followed by a period and one or more word characters.

Author
Hi, my name is Malik Tornes. I am 26 years old and I currently live in Woodland Hills, CA. I am a full stack developer with an advanced skillset in HTML, CSS, and JavaScript. Along with coding I'm also a musician. Below you will see a few of my latest projects on my Github.
https://github.com/malikdreamy



