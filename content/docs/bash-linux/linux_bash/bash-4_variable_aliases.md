---
title: "Bash - 4 - Variables and Aliases"
description: ""
summary: ""
date: 2024-10-22T09:34:02+05:30
lastmod: 2024-10-22T09:34:02+05:30
draft: false
weight: 973
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---




### **Variables and Environment Variables**

In Bash, variables can be defined from the command line and used later in the same shell session or from within a script.  
All variables are typically capitalized.

When a variable is available throughout the environment for use, not just one session or script, it is called an **environment variable**.

##### **`env`**  
The `env` command can be used to see all the environment variables defined (these can vary across distributions).

```bash
sujith@sujith-Latitude-7490:~/Desktop$ env
SHELL=/bin/bash
SESSION_MANAGER=local/sujith-Latitude-7490:@/tmp/.ICE-unix/1537,unix/sujith-Latitude-7490:/tmp/.ICE-unix/1537
QT_ACCESSIBILITY=1
PWD=/home/sujith/Desktop
LOGNAME=sujith
HOME=/home/sujith
USERNAME=sujith
IM_CONFIG_PHASE=1
LANG=en_US.UTF-8
USER=sujith
GNOME_TERMINAL_SERVICE=:1.132
DISPLAY=:0
SHLVL=1
PATH=/home/sujith/.nvm/versions/node/v20.17.0/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
GDMSESSION=ubuntu
DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
NVM_BIN=/home/sujith/.nvm/versions/node/v20.17.0/bin
_=/usr/bin/env
OLDPWD=/home/sujith
```

These environment variables can also be viewed by using **`echo`** where `string` is the name of the environment variable. To output the value of a variable, use the `$` sign before the variable name.

```bash
sujith@sujith-Latitude-7490:~/Desktop$ echo $USER; echo $SHELL; echo $PWD; echo $OLDPWD;
sujith
/bin/bash
/home/sujith/Desktop
/home/sujith
```

---

### **Common Bash Environment Variables**

- **`DESKTOP_SESSION`**: Name of the desktop GUI (e.g., `gnome`)
- **`HISTSIZE`**: Size of the history list (e.g., `1000`)
- **`LANG`**: The specified language and character encoding (e.g., `en_US.UTF-8`)
- **`MAIL`**: Location of the user's main mail storage
- **`OLDPWD`**: The previous working directory (prior to the current one)
- **`PATH`**: List of directories to search for executable programs
- **`PS1`**: Defines the user prompt
- **`SHELL`**: The user’s default shell

**`PATH`** is a crucial environment variable in Linux. It contains a list of directories in which the shell searches for executable programs.
Most are found in `/user/bin    /user/sbin`

```bash
PATH=/home/sujith/.nvm/versions/node/v20.17.0/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
```

Without the `PATH` variable, you would need to specify the full path to the executable before running any command.


---

### **Defining Variables**

To store a value in a variable, use an **assignment statement**.  
The syntax is `VAR=VALUE` with **no spaces** around the equal sign.  
We can define new variables or redefine existing ones.

```bash
$ FIRST=Sujith
$ LAST=kumar
$ echo $FIRST $LAST
Sujith Kumar
```

**Using Single Quotes**:  
When using single quotes (`' '`), the Bash interpreter treats the content literally and does not expand the value of variables.
So it will not apply `$` to retrieve the value from variables.

```bash
$ FULL_NAME='$FIRST $LAST'
$ echo $FULL_NAME
$FIRST $LAST
```

**Using Double Quotes**:  
If there is any blank space in the Value being assigned, then value has to be in `" "`
When using double quotes (`" "`), the Bash interpreter will expand variables.

```bash
$ FULL_NAME="$FIRST $LAST"
$ echo $FULL_NAME
Sujith Kumar
```

If a command like `pwd` is stored in a variable and called, Bash will execute it.

**Escape Character (`\`)**:  
The escape character is used to tell the Bash interpreter to treat the following character literally and not interpret it.  
`\$$AMOUNT` escapes the first `$`, so it is not interpreted as a variable.

**Other Escape Characters**:
- `\\` : outputs a backslash (`\`)
- `\b` : backspace
- `\n` : newline
- `\t` : tab
- `\!` , `\$` , `\&` , `\;` , `\'` , `\"` : escaping special symbols


---

### **Aliases**

An **alias** is used to define a shortcut for a command.  
Similar to defining a variable, name can be assigned to a command to shorten its execution.

To define an alias, use an assignment statement:  
`alias name="command"`  
The name is the alias, and the command is the Linux command it represents.

```bash
alias ..="cd .."
alias ~="cd ~"
alias lss=less
alias sl=ls
alias rm='rm -i'  # -i for interactive mode
```
`rm` is given in single quotes to input the interactive version.

You can view all the predefined aliases by typing `alias`:

```bash
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
alias ls='ls --color=auto'
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
```


To remove an alias, use the `unalias` command:

```bash
unalias ll
```

---