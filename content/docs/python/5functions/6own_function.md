---
title: "05 Functions - 06 Creating Functions"
description: ""
summary: ""
date: 2025-02-11T19:58:45+05:30
lastmod: 2025-02-11T19:58:45+05:30
draft: false
weight: 51
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


**Creating and Importing Your Own Modules**

You can organize your code by writing your own modules:

```python
# my_module.py
def hello(name):
    print(f"Hello, {name}!")

def goodbye(name):
    print(f"Goodbye, {name}!")
```

You can then import these functions into another script:

```python
# main.py
from my_module import hello, goodbye

def main():
    hello("world")  # Calls the hello function
    goodbye("world")  # Calls the goodbye function

if __name__ == "__main__":  # Ensures this block runs only when the file is executed directly
    main()
```

The `if __name__ == "__main__":` block ensures that `main()` only runs when `main.py` is executed directly, not when it’s imported as a module.

---

### **Understanding `__name__` and `__main__`**

In Python, the `__name__` variable is automatically set to `"__main__"` when a file is executed directly. This allows you to control which parts of the script run based on how it's used:

```python
# main.py
def hello(name):
    print(f"Hello, {name}!")

if __name__ == "__main__":
    hello("world")  # Only runs when the file is executed directly
```

If you import `main.py` into another file, the code under `if __name__ == "__main__":` will not execute.

---

### **Using Command-Line Arguments**

You can use `sys.argv` to accept command-line arguments, making your script interactive:

```python
import sys
from my_module import hello

if len(sys.argv) == 2:  # Check if one argument (besides the script name) is passed
    hello(sys.argv[1])  # Pass the argument to the hello function
```

Run the script from the command line like this:

```bash
python main.py John
```

This will print:

```
Hello, John!
```

---

### **Avoiding Code Execution on Import**

You can prevent code from running when importing a file by using the `if __name__ == "__main__":` condition. This ensures that certain code only runs when the script is executed directly:

```python
# main.py
def hello(name):
    print(f"Hello, {name}!")

def main():
    hello("world")

if __name__ == "__main__":
    main()  # Runs only if the script is executed directly
```

Now, if you import `main.py` into another script, the `main()` function won't run automatically.

---

### **Conclusion**

- **Modules** help you organize and reuse code across programs.
- Use `import` to bring functions from modules into your script, and `from ... import ...` for specific functions.
- Create aliases for functions or modules with `as` to simplify your code.
- Use `__name__ == "__main__"` to control code execution based on whether the script is run directly or imported.
- Accept command-line arguments with `sys.argv` to make your script more interactive.

With these concepts, you’ll be able to write cleaner, more modular, and reusable Python code.

---
