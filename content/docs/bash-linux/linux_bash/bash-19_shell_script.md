---
title: "Bash - 19 - Shell Scripting"
description: ""
summary: ""
date: 2024-12-29T16:53:05+05:30
lastmod: 2024-12-29T16:53:05+05:30
draft: false
weight: 989
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


### Objectives
- Write a shell script that runs a command or a series of commands for a fixed set of files.
- Run a shell script from the command line.
- Create a shell script that operates on a set of files defined by the user on the command line.
- Build a pipeline that includes shell scripts.

---

## Shell Script

Shell scripts allow us to automate frequently used commands by saving them in a file, enabling us to execute them later with a single command. In essence, **shell scripts** are small programs.

### Creating a Shell Script
1. Navigate to the desired directory:
   ```bash {frame="none"}
   $ cd alkanes
   ```
2. Create a new shell script file:
   ```bash {frame="none"}
   $ nano middle.sh
   ```
   This opens a file where you can write your commands.

3. Add the following command to the file to extract specific lines:
   ```bash {frame="none"}
   head -n 15 octane.pdb | tail -n 5
   ```
   This command collects lines 11-15 of the file `octane.pdb`.

4. Save and close the file.

### Executing the Script
Once the script is saved, you can execute it using:
```bash {frame="none"}
$ bash middle.sh
```

### Making the Script Flexible
To make the script more versatile, replace the specific file name with `$1`, which represents the first argument passed to the script:
```bash {frame="none"}
head -n 15 "$1" | tail -n 5
```
Now, you can provide different file names as arguments when executing the script:
```bash {frame="none"}
$ bash middle.sh octane.pdb
$ bash middle.sh pentane.pdb
```

### Handling Spaces in Filenames
To ensure the script works with filenames that contain spaces, always enclose `$1` in double quotes:
```bash {frame="none"}
head -n 15 "$1" | tail -n 5
```

### Using Additional Arguments
You can also modify the script to accept line numbers as arguments:
To make sure the numbers for head and tail can be altered by arguments, they can also be taken as `$1 $2 $3` in `middle.sh`.


```bash {frame="none"}
head -n "$2" "$1" | tail -n "$3"
```
Now you can specify the number of lines for `head` and `tail`:
```bash {frame="none"}
$ bash middle.sh pentane.pdb 15 5
# 15 and 5 arguments for head and tail
$ bash middle.sh pentane.pdb 20 5
```

## Adding Comments
To make the script understandable, add comments using the `#` character:
```bash {frame="none"}
# Select lines from the middle of a file.
# Usage: bash middle.sh filename end_line num_lines.
head -n "$2" "$1" | tail -n "$3"
```
Comments are ignored by the shell but provide clarity for users.

## Using `$@` to Process Multiple Files
To handle multiple files, use `$@`, which represents all command-line arguments:
```bash {frame="none"}
$ nano sorted.sh
```
Add the following script to sort files by their length:
```bash {frame="none"}
# Sort files by their length.
# Usage: bash sorted.sh one_or_more_filenames
wc -l "$@" | sort -n
```
Execute the script with multiple files:
```bash {frame="none"}
$ bash sorted.sh *.pdb ../creatures/*.dat
```

### Finding Unique Entries
To find unique species in CSV files, where the species is the second data field, use a loop to process each file:
```bash {frame="none"}
for file in "$@"
do
    echo "Unique species in $file:"
    # Extract species names
    cut -d , -f 2 "$file" | sort | uniq
done
```
This script loops through all provided filenames and extracts unique species from each.

