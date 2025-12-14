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

|  Block   | Purpose        |
| :------: | :------------- |
|   `0`    | Root Directory |
|   `1`    | FAT Table      |
| `2-2047` | Data Blocks    |

---

## ✨ Commands

| File               | Directory     | System             |
| :----------------- | :------------ | :----------------- |
| `create <file>`    | `mkdir <dir>` | `format`           |
| `cat <file>`       | `cd <dir>`    | `chmod <n> <file>` |
| `cp <src> <dst>`   | `pwd`         | `help`             |
| `mv <src> <dst>`   | `ls`          | `quit`             |
| `rm <file>`        |               |                    |
| `append <f1> <f2>` |               |                    |

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

## 💻 Usage

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

| ❌ Do NOT            | ✅ You MAY             |
| :------------------- | :--------------------- |
| Copy for assignments | Study the architecture |
| Submit as your own   | Learn FAT concepts     |

**All rights reserved.** No permission to copy or submit as your own work.

---

<div align="center">

_DV1628/DV1629 Operating Systems • Blekinge Institute of Technology_

</div>
