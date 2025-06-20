
# Regular Expressions (Regex)

Regular expressions are powerful text strings used to define search patterns. They are commonly used across various Linux tools and programming languages to locate and manipulate data.

---

## Symbols

| Name             | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| Letters OR Digits| Characters: Regular characters match.                                       |
| . OR *           | Wildcard: `.` matches any single character. `*` matches zero or more occurrences of the preceding character. |
| ^ OR $           | Anchors: `^` asserts the start of a line. `$` asserts the end of a line.   |
| [] OR [^]        | Character classes: `[]` matches any one character in brackets. `[^]` matches any character not in brackets. |
| + OR ?           | Quantifiers: `+` matches one or more occurrences. `?` matches zero or one occurrence. |
| \               | Escape character: Escapes a metacharacter allowing it to be treated as a literal. |

---

## grep

The `grep` command searches for patterns within files. It is widely used for filtering text using regex patterns.

**Syntax:**
```bash
grep [options] pattern [files]
```

**Example:**
```bash
grep "linux" file.txt
```

---

## sed

`sed` (Stream Editor) is used to perform basic text transformations on an input stream (a file or input from a pipeline).

**Syntax:**
```bash
sed [OPTIONS] 'COMMAND' [INPUTFILE...]
```

**Example:**
```bash
sed 's/linux/Linux/' file.txt
```

---

## awk

`awk` is a scripting language designed for text processing and typically used as a data extraction and reporting tool.

**Syntax:**
```bash
awk options '{action }' file_name
```

**Example:**
```bash
awk -F, '{print $2}' file.csv
```
