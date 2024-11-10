---
title: "Bash - 2 Working With Files"
description: ""
summary: ""
date: 2024-10-22T09:33:16+05:30
lastmod: 2024-10-22T09:33:16+05:30
draft: false
weight: 951
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


## [*mkdir*](/personal-site/docs/bash-linux/command-docs/mkdir) Creating Directories

To create a directory in the current location, use:

```bash {frame="none"}
mkdir [name]  # Make directory
```

`-p` option is used to make Multiple directories.

```bash {frame="none"}
mkdir -p [path/to/nested/directories]  # Creates nested directories

mkdir -p ../project/data ../project/results
```
`ls -R` to list all nested sub directories within a directories.

### Example:
To create a directory `2016` with a subdirectory `data` that contains two directories, `processed` and `raw`:

#### Method 1: Step-by-Step Creation
```bash {frame="none"}
mkdir 2016
mkdir 2016/data
mkdir 2016/data/processed
mkdir 2016/data/raw
```

#### Method 2: Navigating and Creating
```bash {frame="none"}
mkdir 2016
cd 2016
mkdir data
cd data
mkdir processed raw
```

#### Method 3: Using `-p`
```bash {frame="none"}
mkdir -p 2016/data/{processed,raw}  # Creates the full structure in one command
```

To create multiple directories at once:
```bash {frame="none"}
mkdir north south pacific  # Creates three separate directories
```

## Naming Conventions

- Avoid spaces; use `_` or `-` instead.
- Do not start names with `-` to prevent confusion with options/flags.
- Stick to characters: `0-9`, `a-z`, `.`, `-`, `_`. Special characters can have different meanings.
- Use single quotes `' '` for names with spaces or special characters.

### Special Characters:
- **Single Quotes:** Enclosing in single quotes preserves the literal value.
- **Escape Character:** Use `\` to escape special characters, allowing them to be treated literally. It preserves the literal value of the next character that follows, with exception of newline.

## Creating a Text File

### Using the Nano Editor
To create a text file with the `nano` editor:

```bash {frame="none"}
nano draft.txt  # Opens nano for editing
```

Type your content, then save using `Ctrl + O` and exit with `Ctrl + X`. 

*Note:* `nano` is a simple text editor suitable for plain text files. For more complex editing, consider `Emacs`, `Vim`, or graphical editors like `Gedit` or `VS Code`. On Windows, alternatives include `Notepad++` or `Notepad`.

### Using the [*touch*](/personal-site/docs/bash-linux/command-docs/touch) Command
To create an empty file:

```bash {frame="none"}
touch my_file.txt  # Creates a blank text file
```

## Removing Files [*rm*](/personal-site/docs/bash-linux/command-docs/rm-remove)

To remove a file:

```bash {frame="none"}
rm my_file.txt  # Deletes the specified file
```

- Use `rm -i` to prompt for confirmation before deletion.
- `rm` cannot remove directories directly. To remove a directory and its contents, use the recursive `-r` option:

```bash {frame="none"}
rm -r directory_name  # Deletes the directory and all its contents
```

- To remove files matching a pattern (e.g., all `.txt` files) with confirmation:

```bash {frame="none"}
rm -i *.txt  # Prompts for each .txt file
```

*Note:* Shell does not have a trash bin; deleted files are permanently removed.

## Moving Files and Directories [Moving files](/personal-site/docs/bash-linux/command-docs/mv-move)

### Renaming Files
To rename a file or move it to a new location:

```bash {frame="none"}
mv [old] [new]  # Moves or renames a file
```

Examples:
```bash {frame="none"}
mv trial/draft.txt trial/quotes.txt  # Renames draft.txt to quotes.txt
mv draft.txt quotes.txt              # While in Same directory rename
```

*Note:* Moving a file to a directory with the same name will silently overwrite the original. Use `mv -i` to prompt for confirmation.

To move files to a different directory:
```bash {frame="none"}
mv trial/quotes.txt .  # Moves to the current directory
mv sucrose.dat maltase.dat ../raw  # Moves files to the parent directory's raw folder
```

## Copying Files and Directories [cp](/personal-site/docs/bash-linux/command-docs/cp-copy)

To copy a file:

```bash {frame="none"}
cp [old] [new]  # Copies a file
```

Example:
```bash {frame="none"}
cp quotes.txt thesis/quotation.txt  # Copies to a new location
```

To copy a directory and all its contents, use `-r`:

```bash {frame="none"}
cp -r thesis thesis_backup  # Copies the entire directory
```

## Operations with Multiple Files and Directories

To copy or move multiple files, list the files followed by the target directory:
If given more than one file names followed by a directory name(directory as last argument)

```bash {frame="none"}
cp file1.txt file2.txt target_directory/  # Copy multiple files
mv file1.txt file2.txt target_directory/   # Move multiple files
```

Using wildcards can simplify this process:

```bash {frame="none"}
cp *.txt backup/  # Copies all .txt files to backup/
```

```bash {frame="none"}
$ mkdir backup

$ cd cretures/minotaur.dat creatures/unicorn.dat backup/

$ cd minotaur.dat unicorn.dat basilisk.dat
#all three are file names, makes a error, this can be handled by using wildcards.
```

## Wildcards

Wildcards represent unknown characters in commands. 

Common wildcards include:

- **`*`**: Represents zero or more characters.
  - `*.pdb` matches all files ending with `.pdb`.
    `*ethane.pdb` represents ethane and methane.
  - `p*.pdb` matches files starting with `p` and has `.pdb`.
  
- **`?`**: Represents exactly one character.
  - `?ethane.pdb` matches only `methane.pdb`.

### Using Wildcards
When executing commands with wildcards:
```bash {frame="none"}
ls *t*ane.pdb   # Lists files with 't' and 'ane' in their names
cp *dataset* backup/datasets  # Copies all files with 'dataset' in the name

ls *t?ne.*     # gives octane pentane
ls *t??ne.pdb  # ethane methane
ls ethane.*    #only ethane

```

Wildcards can be combined for more specific patterns:
```bash {frame="none"}
ls ???ane.pdb  # Matches any three characters followed by 'ane.pdb'
```
When a shell sees a wildcard it expands the wildcard to create a list of matching filenames before running the preceding command.
*Note:* Be cautious; using wildcards can result in errors if not handled properly (e.g., `*.pdf` in a directory with `.pdb` files).


### Using wildcards for copying
```bash {frame="none"}
$ cp *dataset* backup/datasets
# copy anything having dataset as name to datasets directory inside backups

$ cp *calibration.txt backup/calibration
# copying all calibration files

$ cp 2015-11-* send_to_bob/all_november_files/
# copying just November files

$ cp *-23-dataset* send_to_bob/all_datasets_created_on_23rd/
# just 23rd files
```
