---
title: "Bash - 16 - grep"
description: ""
summary: ""
date: 2024-12-29T16:51:37+05:30
lastmod: 2024-12-29T16:51:37+05:30
draft: false
weight: 987
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



## [*grep*](/personal-site/docs/bash-linux/command-docs/grep)

`grep` stands for "global/regular expression/print." It is a powerful tool for searching text and is commonly used in Unix text editors. `grep` finds and prints lines in files that match a specified pattern.

### Basic Usage
To search for a word in a file:
```bash {frame="none"}
$ grep not haiku.txt
# This retrieves all lines containing 'not' in it.
```

### Searching for Phrases
To search for a specific phrase:
```bash {frame="none"}
$ grep "is not" haiku.txt
```
Using quotes makes it easier to search for phrases or single words:
```bash {frame="none"}
$ grep "not" haiku.txt
```

### Options
- **Word Boundary (`-w`)**: Limits matches to whole words only.
```bash {frame="none"}
$ grep -w "The" haiku.txt
```

- **Line Numbers (`-n`)**: Numbers the results with the line numbers.
```bash {frame="none"}
$ grep -n "it" haiku.txt
```

- **Case Insensitivity (`-i`)**: Makes the search case insensitive.
```bash {frame="none"}
$ grep -n -w -i "the" haiku.txt
```

- **Invert Match (`-v`)**: Inverts the search to get all lines without the specified pattern.
```bash {frame="none"}
$ grep -v -n -w "the" haiku.txt
```

- **Recursive Search (`-r`)**: Searches through all files in the directory and subdirectories.
```bash {frame="none"}
$ grep -r "Yesterday"
```

### Wildcards in `grep` Searches
Regular expressions (regex) allow for more complex pattern matching. 

To find lines with words having 'o' in the second position:
```bash {frame="none"}
$ grep -E "^.o" haiku.txt
```
- `^` anchors the match to the start of the line.
- `.` matches any single character.
- `o` matches the letter 'o'.

### Example Breakdown
- `^.o`: Matches any line starting with any character followed by 'o'.

---

