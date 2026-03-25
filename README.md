# get_next_line - @42cursus

> Reading a line from a fd is way too tedious.

[![norminette](https://img.shields.io/badge/norminette-100%25-brightgreen)](https://github.com/42School/norminette)
[![42](https://img.shields.io/badge/42-cursus-blue)](https://42.fr)
[![BUFFER_SIZE](https://img.shields.io/badge/BUFFER_SIZE-42-blue)](https://github.com/42School/get_next_line)

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

