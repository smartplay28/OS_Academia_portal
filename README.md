# OS Academia Portal

> A multifunctional academic management system built in **C**, utilizing Linux system calls for file locking and socket programming. Supports concurrent access by Students, Faculty, and Administrators through a client-server architecture.

---

## 📌 Project Overview

The Academia Portal is a user-friendly academic management system developed in C, leveraging **Linux system calls** for tasks like file locking and socket programming. It provides a complete role-based platform for students, faculty, and administrators to manage academic information efficiently — all running on a client-server model where multiple users can connect simultaneously without data conflicts.

---

## ✨ Features

### 👤 User Account Management
- All student, faculty, and course details stored in structured files
- Three distinct roles: **Admin**, **Student**, and **Faculty**
- Secure login system for all account holders

### 🔐 Login & Security
- Password-protected login for all users
- Administrator access is separately secured to prevent unauthorized system-wide access
- Passwords can be changed by students and faculty

### 🛡️ Data Locking (Concurrency Control)
- **Read locks** allow multiple users to read data simultaneously
- **Write locks** protect critical sections during data modification
- Ensures data integrity even with concurrent connections — no race conditions

### 🌐 Socket Programming (Client-Server Architecture)
- Server maintains the entire database and handles multiple clients concurrently
- Clients connect over sockets to access their role-specific portal
- Built entirely using Linux socket APIs

---

## 👥 Role-Based Menus

### 🔑 Admin
- Add new students and faculty
- View all student and faculty details
- Activate or block student accounts
- Modify student and faculty information
- Logout

### 🎓 Student
- View all available courses
- Enroll in new courses
- Drop enrolled courses
- View details of enrolled courses
- Change password
- Logout

### 👨‍🏫 Faculty
- View courses currently being offered
- Add new courses to the catalog
- Remove courses from the catalog
- Update course details
- Change password
- Logout

---

## 🏗️ Project Structure

```
OS_Academia_portal/
├── Controllers/
│   ├── AdminController.h       # Admin functionality handler
│   ├── StudentController.h     # Student functionality handler
│   └── FacultyController.h     # Faculty functionality handler
├── database/
│   ├── student_file.txt        # Student records
│   ├── faculty_file.txt        # Faculty records
│   └── ...                     # Other database files
├── Helpers/
│   ├── readWriterHelper.h
│   ├── loginHelper.h
│   ├── logoutHelper.h
│   ├── readLock.h
│   ├── writeLock.h
│   ├── releaseLock.h
│   ├── listFacultyHelper.h
│   ├── listStudentHelper.h
│   └── adminCredentials.h
├── Models/
│   ├── student_struct.h        # Student data structure
│   ├── faculty_struct.h        # Faculty data structure
│   └── course_struct.h         # Course data structure
├── client.c                    # Client-side program
├── server.c                    # Server-side program
├── initialCount.c              # Initial database setup
└── offlineSetter.c             # Offline/status management
```

---

## 🛠️ Tools & Technology

| Tool/Concept | Usage |
|---|---|
| **C Language** | Core development language |
| **Linux System Calls** | File I/O, process management |
| **Socket Programming** | Client-server communication |
| **File Locking (fcntl)** | Read/write locks for concurrency |
| **POSIX APIs** | Threading and process handling |
| **File-based Storage** | Persistent data storage |

---

## 🚀 How to Run

### Prerequisites
- Linux OS (Ubuntu recommended)
- GCC compiler installed

### Step 1 — Compile the Server
```bash
gcc server.c -o server
```

### Step 2 — Compile the Client
```bash
gcc client.c -o client
```

### Step 3 — Initialize the Database
```bash
gcc initialCount.c -o initialCount
./initialCount
```

### Step 4 — Run the Server
```bash
./server
```

### Step 5 — Run the Client (on same or different machine)
```bash
./client
```

### Step 6 — Login
- Enter your credentials (Admin / Student / Faculty)
- Follow the on-screen role-based menu to perform academic tasks

---

## 🔄 System Flow

```
Client connects to Server via Socket
        ↓
Login System (Role Detection)
        ↓
   ┌────┴────┐
   ↓         ↓         ↓
Admin     Student    Faculty
Menu       Menu       Menu
   ↓         ↓         ↓
File Operations with Read/Write Locks
        ↓
Database Updated Safely
```

---

## 📚 OS Concepts Demonstrated

- **Socket Programming** — TCP client-server communication
- **File Locking** — `fcntl()` based read/write locks for concurrent access
- **Concurrency** — Multiple clients served simultaneously by the server
- **Linux System Calls** — `fork()`, `read()`, `write()`, `open()`, `close()`
- **File-based Persistence** — Structured binary file storage for all records

---

## 📜 License

This project was developed for academic purposes as part of an Operating Systems course. Feel free to reference or build upon it with appropriate credit.
