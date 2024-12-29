---
title: "Bash - 6 - Environment and Subshell"
description: ""
summary: ""
date: 2024-10-22T09:34:55+05:30
lastmod: 2024-10-22T09:34:55+05:30
draft: false
weight: 975
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



A shell session consists of an environment that includes all the variables, functions, and other entities defined during the session. 

When a session ends (using `exit`), or when a new session is started within a session (e.g., using `bash`), the entities defined in that session are no longer available. 

However, it is possible to create a new session inside the current one, which is referred to as a **subshell** or a **nested shell**.

A **subshell** allows you to create a new environment for performing tasks without affecting the parent shell. This is useful for executing commands or running scripts without modifying the original session.

A item defined in a shell can be made to persist in the subshell by using `export`.
exporting variables from the parent shell to the subshell, ensuring that they are available within the subshell. However, changes made to variables within the subshell will not affect the parent shell.

```bash
export VAR=value   # Exports the variable to the subshell
```

- `export -f`: Exports a function to the subshell.
- `export -p`: Displays all exported variables.
- `export -n`: Removes the export property from a variable.

---

### **Configuration Files for Shell Sessions**

There are four important configuration files in Linux, two for users and two for system administrators:

The two `profile` files execute for both interactive and non interactive sessions. Non interactive session is one where a shell is needed to run a script but there is no user interaction.

When we login to Linux and open a window, we are running an interactive shell. Then both the `profile` and `bashrc` scripts will execute.

#### For System Administrators:

**`/etc/profile`**: This file is executed for all users when they log in. It defines a function called `pathmunge`. 
It sets up environment variables such as `USER`, `LOGNAME`, `MAIL`, `HOSTNAME`, `PATH`, and other system-wide variables. It is primarily used for system-wide settings.
All defined variables are exported. A `umask` instruction is executed.

**`/etc/bashrc`**: This file is executed for interactive non-login shells. It sets additional environment variables, defines system-wide aliases, and modifies the `PATH` variable. It is a good place to define system-wide functions and aliases.

#### For Users:

**`~/.bash_profile`**: This file is executed for login shells. It typically contains an `if` statement that checks if the user’s `.bashrc` exists, and if so, runs it. It can also be used for user-specific environment variables.

**`~/.bashrc`**: This file is executed for non-login interactive shells. It is where users can define their own functions, aliases, and environment variables. It also sources `/etc/bashrc` to include system-wide settings.

---

### **How Shell Configuration Files Work**

When a user logs in:

1. **`/etc/profile`** is executed first. This file typically contains functions like `pathmunge` to construct the `PATH` variable and defines environment variables like `USER`, `LOGNAME`, `MAIL`, and others. It also executes `umask` to set file creation permissions.
2. **`/etc/bashrc`** is executed next, setting additional environment variables and modifying the `PATH`. It is where system-wide aliases and functions should be defined.

Then, **`~/.bash_profile`** executes:

- It checks if the `.bashrc` file exists in the user’s home directory, and if so, sources it to run the user-specific configuration.

**`~/.bashrc`**:

- It checks if `/etc/bashrc` exists and sources it, even though it may have already been executed by `/etc/profile`. This file concludes by adding local `bin` directories (`$HOME/.local/bin` and `$HOME/bin`) to the `PATH` variable.
- You can add custom aliases and functions in this file.

---

### **Logout and Session Cleanup**

- **`~/.bash_logout`**: This file is invoked when a Bash session is closed. Users can define commands to run before the session ends, such as cleaning up temporary files or logging out of remote sessions.

Changes made to these configuration files do not take effect until a new session is started. To apply changes immediately within the current session, the **`source`** command can be used to reload a script:

```bash
source ~/.bashrc
```

---

### **Text Editors: `vi` and `vim`**

**`vi`** (or its improved version **`vim`**) is the default text editor found in most Linux distributions. It is used for editing text files from the command line. `vim` (Vi IMproved) offers additional features like syntax highlighting, better search functionalities, and more. While `vi` is still widely used, `vim` is recommended due to its enhanced capabilities.

---

### **Compiler vs Interpreter**

- **Compiler**: A compiler translates the entire source code of a program into machine code (binary code) that can be executed by the computer. It produces an independent executable file.
- **Interpreter**: An interpreter directly executes instructions written in a programming language, without converting them into machine code beforehand. It processes the code line by line.

Some languages, like Java, use an intermediate **bytecode**, which is platform-independent. The bytecode is then interpreted by the Java Virtual Machine (JVM), making the code portable across different systems.

---