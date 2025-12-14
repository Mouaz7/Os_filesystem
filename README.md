<div align="center">

# 🗂️ OS Filesystem

[![C++](https://img.shields.io/badge/C++-11-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)](https://isocpp.org/)
[![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)](https://www.linux.org/)
[![BTH](https://img.shields.io/badge/BTH-DV1628/DV1629-purple?style=for-the-badge)](https://www.bth.se/)

**FAT-based file system implementation with interactive shell**

</div>

---

## 🎯 Overview

A complete simulated file system demonstrating OS concepts:

- **Block storage** with FAT (File Allocation Table)
- **Hierarchical directories** with subdirectory support
- **Unix-like permissions** (read/write/execute)
- **Path resolution** (absolute & relative paths)
- **8 MB virtual disk** (2048 blocks × 4 KB)

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────┐
│         Interactive Shell (shell.cpp)   │
├─────────────────────────────────────────┤
│         File System Core (fs.cpp)       │
│   FAT Table │ Directories │ Paths       │
├─────────────────────────────────────────┤
│         Disk Layer (disk.cpp)           │
├─────────────────────────────────────────┤
│         diskfile.bin (8 MB)             │
└─────────────────────────────────────────┘
```

| Block ID | Content            | Size  | Description                           |
| :------: | :----------------- | :---- | :------------------------------------ |
|   `0`    | **Root Directory** | 4 KB  | Entry point for the file hierarchy    |
|   `1`    | **FAT Table**      | 4 KB  | Tracks used/free blocks & file chains |
| `2-2047` | **Data Blocks**    | ~8 MB | Stores actual file content            |

---

## ✨ Commands

### 📂 File Operations

| Command    | Usage                | Description                           |
| :--------- | :------------------- | :------------------------------------ |
| **create** | `create <file>`      | Create a new file (opens editor mode) |
| **cat**    | `cat <file>`         | Display the contents of a file        |
| **cp**     | `cp <src> <dst>`     | Copy a file to a new location         |
| **mv**     | `mv <src> <dst>`     | Move or rename a file                 |
| **rm**     | `rm <file>`          | Remove/delete a file                  |
| **append** | `append <src> <dst>` | Append content of `src` to `dst`      |
| **chmod**  | `chmod <mod> <file>` | Change file permissions (e.g. `111`)  |

### 📁 Directory Operations

| Command   | Usage         | Description                          |
| :-------- | :------------ | :----------------------------------- |
| **mkdir** | `mkdir <dir>` | Create a new directory               |
| **cd**    | `cd <dir>`    | Change current directory             |
| **pwd**   | `pwd`         | Print current working directory path |
| **ls**    | `ls`          | List files in current directory      |

### ⚙️ System

| Command    | Usage    | Description                               |
| :--------- | :------- | :---------------------------------------- |
| **format** | `format` | Format the virtual disk (erases all data) |
| **help**   | `help`   | Show available commands                   |
| **quit**   | `quit`   | Exit the shell                            |

---

## 🚀 Build & Run

```bash
git clone https://github.com/Mouaz7/Os_filesystem.git
cd Os_filesystem
make
./filesystem
```

**Run tests:**

```bash
make runtests
```

---

## 💻 Usage Example

```bash
filesystem> format
filesystem> mkdir docs
filesystem> cd docs
filesystem> create hello.txt
Enter data. Empty line to end.
Hello World!

filesystem> cat hello.txt
Hello World!
filesystem> pwd
/docs
```

---

## 📁 Project Structure

```
├── main.cpp          # Entry point
├── shell.cpp/h       # Shell interface
├── fs.cpp/h          # File system core
├── disk.cpp/h        # Disk I/O
├── Makefile          # Build config
└── test_script*.cpp  # Test suite
```

---

## ⚠️ Academic Integrity

<div align="center">

```
⛔ DO NOT COPY THIS CODE ⛔
```

</div>

This code was developed as a **graded lab assignment** at BTH.

| ✅ You MAY                       | ❌ You MUST NOT                        |
| :------------------------------- | :------------------------------------- |
| Study the architecture and logic | Copy code for your own assignments     |
| Learn FAT file system concepts   | Submit this project as your own work   |
| Run and test the code locally    | Plagiarize any part of this repository |

**All rights reserved.** File system concepts are universal, but this specific implementation is protected.

---

<div align="center">

_DV1628/DV1629 Operating Systems • Blekinge Institute of Technology_

</div>
