# To Understand the Email Regex: Breaking Down the Pattern

This tutorial breaks down a common regular expression used to validate email addresses. 
We will explore each of these part of the regex to understand how it ensures an email address is correctly formatted. 


## Summary

The regex pattern `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` this is designed to validate email addresses. 
This pattern ensures that an email address:

- Begins with one or more characters that can include lowercase letters, numbers, underscores (`_`), dots (`.`), and hyphens (`-`).
- Contains an `@` symbol followed by a valid domain name.
- Ends with a domain extension such as `.com`, `.net`, or `.io`.

By understanding each component, you'll gain insight into how this regex effectively validates email addresses.


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)




## Regex Components


### Anchors
The Anchors defines the position of the pattern thats within a string

- `^` — The caret symbol asserts that the match must start at the **beginning** of the string.
- `$` — The dollar symbol asserts that the match must end at the **end** of the string.

In the email regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, these anchors ensure that the entire email address is validated from start to finish.

**For Example:**
-  `user.name@example.com` (Valid)
-  `This user.name@example.com` (Invalid – extra text at the start)
-  `user.name@example.com those` (Invalid – extra text at the end)




### Quantifiers
Quantifiers specify how many times a character, group, or character class must appear

- `+` — Matches **one or more** of the preceding token.
- `{2,6}` — Matches **between 2 and 6** characters.

In the email regex:
- `[a-z0-9_\.-]+` ensures the username portion has **one or more** valid characters.
- `[a-z\.]{2,6}` ensures the domain extension is **2 to 6 characters** long (example; ,`.io`,`.net`,`.com` ).

**For Example:**
-  `jane_doe123@example.io` (Valid)
-  `jane@ex.co` (Invalid –  domain extension must be **at least 2 characters** and **no more than 6**)






### Character Classes
Character classes define sets of characters that can match.

- `[a-z0-9_\.-]` — Matches **lowercase letters**, **numbers**, underscores (`_`), dots (`.`), and hyphens (`-`).
- `[\da-z\.-]` — Matches **digits**, **lowercase letters**, dots (`.`), and hyphens (`-`).
- `[a-z\.]` — Matches **lowercase letters** and dots (`.`).

The Character classes allow for the regex to flexibly capture valid email, username, and domain structures.

**For Example:**
-  `andy_123@gmail.com` (Valid)
-  `Andy_123@Gmail.com` (Invalid – uppercase letters are not included in the character class)




### Grouping and Capturing
Grouping allows for multiple characters to be treated as a single unit, while capturing stores the matched content.

- `()` — Captures the content inside the parentheses.

In the email regex:
- `([a-z0-9_\.-]+)` captures the **username**.
- `([\da-z\.-]+)` captures the **domain name**.
- `([a-z\.]{2,6})` captures the **domain extension**.

**For Example:**
- Captured Groups for `andy.zuni123@gmail.com`:
  - Group 1: `andy.zuni123`
  - Group 2: `gmail`
  - Group 3: `com`




### Bracket Expressions
Bracket expressions are similar to character classes and define a set of possible characters.

In the email regex:
- `[a-z0-9_\.-]` this specifies valid characters in the username.
- `[\da-z\.-]` this specifies valid characters in the domain name.
- `[a-z\.]` this specifies valid characters in the domain extension.

**For Example:**
-  `user.name@example.com` (Valid)
-  `user@exam__e.com` (Invalid – underscore is not allowed in the domain)




### Greedy and Lazy Match
Greedy and lazy quantifiers wil determine how much text the regex captures.

- `+` is **greedy**, meaning it will match **as much text as possible**.
- `?` can be added after a quantifier to make it **lazy**, meaning it will match **as little text as possible**.

In the email regex, the `+` quantifier is greedy so then it will ensure it captures as much valid content as possible for the username, domain, and extension.

**For Example:**
-  `username@gmail.com` (Valid)
-  `user.name@example.co.uk` (Valid — greedy matching captures both `.co` and `.uk`)




## Author
This tutorial was created by [Luis Then].  
I'm a web development student passionate about improving my coding skills and my sharing knowledge with others.  
You can find more of my projects here in my GitHub profile:  https://github.com/Samuelthenm