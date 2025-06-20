# 📄 get_next_line

`get_next_line` reads and returns one line at a time from a file descriptor, implemented from scratch as part of the 42 School curriculum.
It handles dynamic line lengths using a buffer of configurable size and static variables to maintain state between calls.

## 🔧 Overview
- Language: **C**  
- Norm-compliant (42 coding style rules)  
- Uses `read()`, `malloc()`, and `free()` only  
- Supports `-D BUFFER_SIZE=n` compile-time option  

## 🧠 Core Concepts
- Efficient file I/O using `read()` with fixed-size buffer  
- Use of **static variables** for maintaining the leftover buffer  
- Handling of newlines and end-of-file conditions  
- Robust error detection and memory management  
- Correct behavior with both files and standard input  

<br>

## 📋 Functionality
Implements `char *get_next_line(int fd);` that:
- Returns the next line read from `fd`, **including** the newline character if present  
- Returns `NULL` at end-of-file or on error  
- Works correctly in loops reading multiple lines  
- Reads up to `BUFFER_SIZE` bytes per `read()` call  
- Avoids undefined behavior with binary files or modified inputs  

<br>

## 📦🚀 How to Use
Clone and compile:
```bash
git clone https://github.com/IzaroArbaiza/get_next_line.git
cd get_next_line && make
```

### 👉🏼 Usage
Add the next lines to your code
```C
#include "get_next_line.h"

int fd = open("file.txt", O_RDONLY);
char *line;
while ((line = get_next_line(fd))) {
    printf("%s", line);
    free(line);
}
close(fd);
```

Compile with:
```bash
gcc your_file.c get_next_line.c get_next_line_utils.c -D BUFFER_SIZE=42 -I. && ./a.out
```
