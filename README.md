# customised-virtual-file-system
Linux-like virtual file system implemented in C to simulate core file system operations using OS internals.

# Customised Virtual File System (CVFS)

## Overview
The Customised Virtual File System (CVFS) is a Linux-inspired, in-memory virtual file system implemented in C using system programming and operating system internals.  
It simulates core file system operations such as file creation, deletion, reading, writing, permission handling, and inode management without interacting with physical disk storage.

This project helps in understanding how file systems internally manage files using inodes, file tables, and user file descriptor tables.

---

## Key Objectives
- Understand the internal working of UNIX/Linux file systems  
- Implement inode-based file management  
- Simulate file-related system calls in user space  
- Strengthen system programming and OS concepts  

---

## Technology Stack
- Programming Language: C  
- Domain: System Programming  
- Core Concepts:  
  - File Systems  
  - Inodes  
  - File Tables  
  - Permissions  
  - Linked Lists  
- Reference: *Advanced UNIX System Programming* — W. Richard Stevens  

--- 

## User Interface
- Command Line Interface (CLI)  
- Interactive shell-based interface (Marvellous CVFS : >)

---

## Features Implemented
- Creation of regular files with permissions  
- File descriptor-based file handling  
- Read and write operations with offset management  
- File deletion using unlink mechanism  
- File listing with inode details  
- Permission validation (READ / WRITE)  
- In-memory file storage using buffers  

---

## Supported Commands
creat <filename> <permission>
ls
write <fd>
read <fd> <size>
unlink <filename>
man <command>
help
clear
exit


---

## Internal Data Structures

### SuperBlock
Maintains:
- Total number of inodes
- Number of free inodes

### Inode (DILB)
Stores:
- File name
- Inode number
- File size and actual file size
- File type
- Reference count
- Permissions
- Buffer for file data
- Pointer to next inode

### File Table
Stores:
- Read offset
- Write offset
- Access mode
- Pointer to inode

### UAREA (User Area)
- Process name
- User File Descriptor Table (UFDT)

---

## Architecture Overview
         +-------------+
         |  BootBlock  |
         +-------------+
                |
                v
         +-------------+
         | SuperBlock  |
         +-------------+
                |
                v
 +---------------------------+
 | Incore Inode Table (DILB) |
 |   (Linked List of Inodes) |
 +---------------------------+
                |
                v
         +-------------+
         | File Table  |
         +-------------+
                |
                v
 +------------------------------+
 | UFDT (User File Descriptor)  |
 +------------------------------+

---

## Execution Flow
1. Initialize BootBlock, SuperBlock, DILB, and UAREA  
2. Start the CVFS interactive shell  
3. Accept user commands  
4. Validate command and parameters  
5. Perform file operations  
6. Update internal data structures  
7. Display output or error message  

---

## Error Handling
The project implements structured error handling using predefined error codes such as:
- ERR_INVALID_PARAMETER  
- ERR_FILE_ALREADY_EXIST  
- ERR_FILE_NOT_EXIST  
- ERR_PERMISSION_DENIED  
- ERR_INSUFFICIENT_SPACE  
- ERR_MAX_FILES_OPEN  

---

## Limitations
- In-memory file system (no persistent storage)  
- Single-user environment  
- No directory hierarchy  
- Fixed inode and file size limits  

---

## Future Enhancements
- Disk-based persistent storage  
- Directory structure support  
- Multi-user access control  
- Improved permission and security model  

---

## Learning Outcomes
- Clear understanding of file system internals  
- Practical experience with inode-based design  
- Strong foundation in system programming  
- Improved readiness for OS and Linux interviews  

---

## Author
Siddhi Unawane  
Bachelor of Engineering — Computer Engineering  

---

## Note
This project is developed for educational purposes to demonstrate core operating system and system programming concepts.


