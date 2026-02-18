#Tuition Management System

A web-based Tuition Management System built with **PHP**, **MySQL**, and **Bootstrap**. This system allows administrators to manage tutors, students, subjects, classes, bookings, and payments — while students can book classes, view schedules, and manage their payments.

---

##Tech Stack

- **Frontend:** HTML, CSS, Bootstrap 5, Google Fonts (Poppins)
- **Backend:** PHP (procedural)
- **Database:** MySQL
- **Local Server:** XAMPP / WAMP / MAMP

---

##User Roles

| Role | Access |
|------|--------|
| **Admin** | Manage students, tutors, subjects, classes, bookings, payments |
| **Student** | Book classes, view schedule, track bookings, make payments |

---

##Features

### Admin
- Dashboard overview
- Manage Students (Add, Edit, Delete)
- Manage Tutors (Add, Edit, Delete)
- Manage Subjects (Add, Edit, Delete)
- Manage Classes (Add, Edit, Delete)
- Manage Bookings (Approve, Reject, Edit, Delete)
- Payment Management (Mark as Paid)
- View Calendar / Schedule

### Student
- Personal Dashboard
- Book a Class
- View My Bookings
- View My Schedule & Calendar
- Payment tracking
- Profile management

---

## How to Run Locally

### 1. Requirements
- Laragon 6.0
- PHP 7.4+
- MySQL 5.7+

### 2. Clone or Download the Project
```bash
git clone https://github.com/addy0us/tuition-system.git
```
Or download the ZIP and extract it.

### 3. Move to Web Server Directory
Copy the `tuition_system` folder into:
- **Laragon:** `C:/laragon/www/`


### 4. Import the Database
1. Open your browser and go to `http://localhost/phpmyadmin`
2. Create a new database named `tuition_system`
3. Click **Import**, select the `tuition_system.sql` file from the project folder, and click **Go**

### 5. Configure Database Connection
Open `config/db.php` and make sure the credentials match your setup:
```php
$host = "localhost";
$user = "root";
$pass = "";         // no password, just enter
$db   = "tuition_system";
```

### 6. Run the System
Open your browser and go to:
```
http://localhost/tuition_system/
```

---

Default Login

> You may need to create an admin account manually via phpMyAdmin or use the `hash.php` file included to generate a hashed password.

| Field | Value |
|-------|-------|
| URL | `http://localhost/tuition_system/auth/login.php` |
| Role | admin / student |

---

## Project Structure

```
tuition_system/
├── admin/              # Admin-side pages (students, tutors, classes, bookings, payments)
│   └── student/        # Admin view of student portal
├── auth/               # Login & logout
├── assets/             # Images and static assets
├── config/             # Database connection
├── includes/           # Shared header & footer
├── student/            # Student-side pages (booking, schedule, payment, profile)
├── index.php           # Landing page
├── hash.php            # Password hashing utility
└── tuition_system.sql  # Database dump
```

---

## Security Features

- Passwords hashed using `password_hash()` / `password_verify()` (bcrypt)
- Prepared statements used to prevent SQL injection
- Session-based role authentication on every page
- Role-based access control (admin vs student)

---

##Database Indexing

Indexes have been applied on frequently queried columns to optimize performance:

- `users.email` — UNIQUE index for fast login lookups
- `users.role` — Index for role-based filtering (`idx_user_role`)
- `bookings.student_id` — Index for student booking queries
- `class.subject_id` — Index for class/subject JOIN queries

---

## License

This project was developed as part of the **IMS560 Advanced Database Management System** group assignment.