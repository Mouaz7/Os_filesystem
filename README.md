<div align="center">

# 🗂️ OS Filesystem

[![C++](https://img.shields.io/badge/C++-11-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)](https://isocpp.org/)
[![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)](https://www.linux.org/)

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

```mermaid
graph TD
    subgraph Application
        Shell[Interactive Shell (shell.cpp)]
    end

    subgraph File_System
        FS[File System Core (fs.cpp)]
        Meta[FAT Table | Directories | Paths]
    end

    subgraph Driver
        Disk[Disk Layer (disk.cpp)]
    end

    subgraph Hardware
        Bin[("diskfile.bin (8 MB)")]
    end

    Shell --> FS
    FS --- Meta
    FS --> Disk
    Disk --> Bin
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
