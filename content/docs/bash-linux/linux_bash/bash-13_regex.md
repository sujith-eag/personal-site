---
title: "Bash - 13 - Regular Expressions"
description: ""
summary: ""
date: 2024-12-29T16:50:36+05:30
lastmod: 2024-12-29T16:50:36+05:30
draft: false
weight: 982
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


A regular expression (regex) is a string that expresses a pattern.
Contains combination of literal characters and meta-characters.
The meta-characters modify the literal characters to provide variability.

The result is that a regex can match more than just a literal string.
regex are used to search for strings for pattern of interest.

`"aeiou"` matches only a string. 
`"[aeiou]{5}"` this regex will match any string of vowels in lower case (word with five consecutive vowels in any order) using `pattern matching`

Wild cards allow one way to express patterns, but regex allow for expressing more complex patterns. Some wild card characters are used but their usage differs.


### Metacharacters

The regex of Linux was adopted from POSIX (Portable Operating System Interface for Unix) which was the series of standards that OS developers should impliment to ensure `Unix or Unix like` OS shared features.

Original metacharacters described by POSIX make up the `basic regularexpression` set.
Later `extended regular expression` was defined by POSIX with same set of metacharacters but without the `\` for some characters.




