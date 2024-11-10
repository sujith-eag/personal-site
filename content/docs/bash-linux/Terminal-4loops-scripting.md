---
title: "Bash - 4 Loops Scripting"
description: ""
summary: ""
date: 2024-10-22T09:34:02+05:30
lastmod: 2024-10-22T09:34:02+05:30
draft: false
weight: 953
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


### Objectives
- Write a loop that applies to one or more commands separately to each file in a set of files.
- Trace the values taken by a loop variable during the execution of the loop.
- Explain the difference between a variable's name and its value.
- Explain why spaces and some punctuation characters shouldn't be used in filenames.
- Demonstrate how to see what commands have recently been executed.
- Run recently executed commands without retyping them.

---

## Loops

Loops are programming constructs that allow us to repeat a command or set of commands for each item in a list.

### Basic Loop Structure
```bash {frame="none"}
for filename in basilisk.dat minotaur.dat unicorn.dat
do
    echo $filename
    head -n 2 $filename | tail -n 1
done
```
- `for` indicates the start of the loop.
- `do` begins the block of commands to execute.
- `done` marks the end of the loop.
- `$` is used to denote a variable that will be replaced by its value.

### Example: Echoing Numbers
```bash {frame="none"}
for number in 0 1 2 3 4 5 6 7 8 9
do
    echo $number
done
```

### Common Mistakes
**Incorrect Method:**
```bash {frame="none"}
for data in *.pdb
do
    ls *.pdb
done
```
*This prints all `.pdb` files repeatedly.*

**Correct Method:**
```bash {frame="none"}
for data in *.pdb
do
    ls $data
done
```
*This prints each file individually.*

### Filtering Files
To print only specific files:
```bash {frame="none"}
for filename in c*   # to print cubane.pdb
do
    ls $filename
done
```
*This prints files starting with 'c'.*

To print files that contain 'c':
```bash {frame="none"}
for filename in *c*
do
    ls $filename
done
```

## Saving Output to a File in a Loop
```bash {frame="none"}
for alkanes in *.pdb
do
    echo $alkanes
    cat $alkanes >> alkanes.pdb
done
```
*This appends the contents of all `.pdb` files into `alkanes.pdb`. Using `>` would overwrite the file each time.*

## Piping
You can combine commands using a pipe (`|`):
```bash {frame="none"}
for filename in *.dat
do
    echo $filename
    head -n 100 $filename | tail -n 20
done
```
*This outputs the last 20 lines from the first 100 lines of each `.dat` file.* So gives lines from 81 to 100.

## Handling Spaces in Filenames
When dealing with filenames that contain spaces, enclose them in quotes:
```bash {frame="none"}
for filename in "red dragon.dat" "purple unicorn.dat"
do
    head -n 100 "$filename" | tail -n 20
done
```
*Note: Do not enclose `$filename` in quotes inside the loop.*

## Copying Files into Multiple Files
Using a wildcard directly with `cp` may raise errors:
```bash {frame="none"}
cp *.dat original-*.dat
```
*This fails if there are multiple files or last argument is not a directory.*

Using a loop:
```bash {frame="none"}
for filename in *.dat
do
    cp "$filename" "original-$filename"
done
```
*This copies each `.dat` file with a prefix of `original-`.*
Now each of `.dat` file come one by one and in the cp there will be only two files,   
so will be copied into the other.


## Scripting
Example of a loop in a script:
```bash {frame="none"}
for datafile in NENE*A.txt NENE*B.txt
do
    bash goostat.sh "$datafile" "stats-$datafile"
done
```
*This runs a script for each specified file.*

To echo commands without executing them:
```bash {frame="none"}
for datafile in *.dat
do
    echo "cat $datafile >> all.pdb"
done
```
*Using quotes here prevents the command from executing immediately.*

## Nested Loops
You can nest loops to perform more complex tasks:
```bash {frame="none"}
for species in cubane ethane methane
do
    for temp in 25 30 37 40
    do
        mkdir "$species-$temp"
    done
done
```
*This creates directories named after each species combined with the temperature.*
