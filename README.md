<div align="center">

# 🗂️ OS Filesystem

[![C++](https://img.shields.io/badge/C++-11-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)](https://isocpp.org/)
[![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)](https://www.linux.org/)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

**FAT-based file system implementation with interactive shell**

[Features](#-overview) • [Commands](#-commands) • [Build](#-build--run) • [Usage](#-usage-example)

</div>

---

## 🎯 Overview

A complete simulated file system demonstrating OS concepts:

| Feature                         | Description                                  |
| :------------------------------ | :------------------------------------------- |
| 💾 **Block Storage**            | FAT (File Allocation Table) based allocation |
| 📂 **Hierarchical Directories** | Full subdirectory support                    |
| 🔐 **Unix-like Permissions**    | Read, write, execute flags                   |
| 🛣️ **Path Resolution**          | Both absolute & relative paths               |
| 💿 **Virtual Disk**             | 8 MB disk (2048 blocks × 4 KB)               |

---

## 🏗️ Architecture

```
┌────────────────────────────────────────┐
│           shell.cpp (User Interface)   │
└────────────────────┬───────────────────┘
                     │
                     ▼
┌────────────────────────────────────────┐
│              fs.cpp (Core)             │
│    ┌─────────────┬─────────────────┐   │
│    │  FAT Table  │   Directories   │   │
│    └─────────────┴─────────────────┘   │
└────────────────────┬───────────────────┘
                     │
                     ▼
┌────────────────────────────────────────┐
│           disk.cpp (I/O Layer)         │
└────────────────────┬───────────────────┘
                     │
                     ▼
┌────────────────────────────────────────┐
│         diskfile.bin (8 MB)            │
└────────────────────────────────────────┘
```

### 📊 Disk Layout

| Block  | Purpose        | Size  |
| :----: | :------------- | :---- |
|   0    | Root Directory | 4 KB  |
|   1    | FAT Table      | 4 KB  |
| 2-2047 | Data Blocks    | ~8 MB |

---

## ✨ Commands

<table>
<tr>
<td valign="top">

### 📂 Files

| Command            | Description       |
| :----------------- | :---------------- |
| `create <file>`    | Create new file   |
| `cat <file>`       | Show file content |
| `cp <src> <dst>`   | Copy file         |
| `mv <src> <dst>`   | Move/rename file  |
| `rm <file>`        | Delete file       |
| `append <f1> <f2>` | Append f1 to f2   |
| `chmod <n> <file>` | Set permissions   |

</td>
<td valign="top">

### 📁 Directories

| Command       | Description      |
| :------------ | :--------------- |
| `mkdir <dir>` | Create directory |
| `cd <dir>`    | Change directory |
| `pwd`         | Print path       |
| `ls`          | List contents    |

### ⚙️ System

| Command  | Description |
| :------- | :---------- |
| `format` | Format disk |
| `help`   | Show help   |
| `quit`   | Exit shell  |

</td>
</tr>
</table>

---

## 🚀 Build & Run

```bash
# Clone and build
git clone https://github.com/Mouaz7/Os_filesystem.git
cd Os_filesystem
make

# Run the filesystem
./filesystem

# Run tests
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
Os_filesystem/
├── main.cpp           # Entry point
├── shell.cpp/.h       # Interactive shell
├── fs.cpp/.h          # File system core
├── disk.cpp/.h        # Disk I/O layer
├── Makefile           # Build configuration
└── test_script*.cpp   # Test suite
```

---

<div align="center">

**Made with ❤️ using C++**

</div>
