# get_next_line


[![norminette](https://img.shields.io/badge/norminette-OK-brightgreen)](https://github.com/42School/norminette)
[![42](https://img.shields.io/badge/42-cursus-blue)](https://42.fr)
[![BUFFER_SIZE](https://img.shields.io/badge/BUFFER_SIZE-n-blue)](https://github.com/42School/get_next_line)

## 📖 Introduction

The goal of this project is to write a function that returns a line read from a file descriptor. Whether it's a text file, standard input, or even a network connection, your function must allow you to read the content **one line at a time** until the end of the data.

This project introduces the concept of **static variables** in C programming, which are essential for "remembering" data (the remainder of a buffer) between successive function calls.

> **Key takeaway:** Understanding static variables and efficient buffer management is crucial for building robust I/O functions.

---

## 🎯 Project Objectives

- Understand static variables and their lifecycle
- Implement efficient buffer management with `BUFFER_SIZE`
- Handle file descriptors properly
- Manage memory without leaks
- Handle edge cases (empty files, no newline, etc.)
- **Bonus**: Support multiple file descriptors simultaneously

---

## 🛠️ Technical Considerations

### Function Prototype
```c
char *get_next_line(int fd);
```

## Allowed External Functions

| Function | Purpose |
|----------|---------|
| `read` | Read data from a file descriptor |
| `malloc` | Dynamic memory allocation |
| `free` | Memory deallocation |

## Static Variables

You must use at least one static variable to preserve data between calls:

```c
static char *stash;  // Stores leftover data between reads
```

### Memory Management

    - The function returns the line read (including \n if present)

    - If there's nothing else to read or an error occurs, returns NULL

    - All allocated memory must be properly freed

### Buffer Size
``` bash
The compilation must work with the flag -D BUFFER_SIZE=n:
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line.c main.c
```
## 🌟 Bonus Features

### The bonus part has two strict requirements that elevate your implementation:
1. Single Static Variable

You must develop get_next_line using only one static variable. This forces you to think creatively about data structures.
2. Multiple File Descriptors

Your function must manage multiple file descriptors simultaneously. You can read from fd 3, then fd 4, then fd 5, and then go back to fd 3—the function will remember exactly where it left off in each file without mixing up the data.
``` c
// Example: Reading from multiple FDs alternately
line1 = get_next_line(fd1);  // Reads line from file 1
line2 = get_next_line(fd2);  // Reads line from file 2  
line3 = get_next_line(fd1);  // Continues where it left off in file 1
```
### Implementation Strategy

To handle multiple FDs with a single static variable, we use an array (or a linked list) where the index corresponds to the file descriptor:
``` c
static char *stash[OPEN_MAX];  // One pointer per possible FD
```


## 📥 Getting Started

### 🔧 Clone the Repository

To get a local copy of the project, run:

```bash
# Clone the repository
git clone https://github.com/masselgu/get_next_line.git

# Navigate to the project directory
cd get_next_line

# Build the library
make
```
