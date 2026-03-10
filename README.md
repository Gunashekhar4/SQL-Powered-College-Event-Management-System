# 🎓 College Event Management System

<div align="center">

![PHP](https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![XAMPP](https://img.shields.io/badge/XAMPP-FB7A24?style=for-the-badge&logo=xampp&logoColor=white)

A web-based platform for organizing and managing college events — built with PHP & MySQL.

</div>

---

## 📌 Overview

The **College Event Management System** eliminates the chaos of manual event coordination. It gives students a seamless way to discover and register for events, while admins get a full-control dashboard to manage everything from creation to participation.

> Designed for college fests, workshops, seminars, gaming events, and more.

---

## ✨ Features

### 👤 For Users
- Register and log in securely
- Browse events by category (Technical, Gaming, On Stage, Off Stage)
- Register for events with personal and college details
- View and manage all registered events from a personal dashboard

### 🛠️ For Admins
- Full-featured admin dashboard
- Create, update, and delete events
- Manage event types and participant lists
- Real-time overview of all registrations

### 🔒 Security
- SQL injection prevention via **prepared statements**
- Secure PHP session management
- Password hashing for all user credentials

---

## 🧱 Tech Stack

| Layer | Tech |
|---|---|
| Frontend | HTML5, CSS3, JavaScript, Bootstrap |
| Backend | PHP |
| Database | MySQL |
| Local Server | XAMPP / WAMPP |

---

## 🗄️ Database Schema

Three core tables power the system:

```sql
-- Events
CREATE TABLE `events` (
  `event_id`    int(100) NOT NULL AUTO_INCREMENT,
  `event_title` text NOT NULL,
  `event_price` int(20) NOT NULL,
  `participents` int(100) NOT NULL,
  `img_link`    text NOT NULL,
  `type_id`     int(100) NOT NULL,
  PRIMARY KEY (`event_id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

-- Event Categories
CREATE TABLE `event_type` (
  `type_id`    int(10) NOT NULL AUTO_INCREMENT,
  `type_title` text NOT NULL,
  PRIMARY KEY (`type_id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

-- Participants / Registrations
CREATE TABLE `participants` (
  `p_id`      int(10) NOT NULL AUTO_INCREMENT,
  `event_id`  int(10) NOT NULL,
  `fullname`  varchar(100) NOT NULL,
  `email`     varchar(300) NOT NULL,
  `mobile`    varchar(10) NOT NULL,
  `college`   varchar(300) NOT NULL,
  `branch`    varchar(11) NOT NULL,
  PRIMARY KEY (`p_id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

<details>
<summary>📦 View sample seed data</summary>

```sql
INSERT INTO `events` (`event_title`, `event_price`, `participents`, `img_link`, `type_id`) VALUES
('pubg', 50, 4, 'cs01.jpg', 2),
('tech quiz', 50, 2, 'cs02.jpg', 1),
('counter strike', 50, 1, 'cs03.jpg', 2),
('pair programming', 50, 2, 'cs01.jpg', 1),
('seminar', 50, 1, 'cs02.jpg', 3),
('multiple choice', 50, 1, 'cs01.jpg', 4);

INSERT INTO `event_type` (`type_title`) VALUES
('Technical Events'),
('Gaming Events'),
('On Stage Events'),
('Off Stage Events');
```
</details>

---

## 🚀 Getting Started

### Prerequisites
- [XAMPP](https://www.apachefriends.org/download.html) (includes Apache + MySQL + PHP)
- Git

### Installation

**1. Clone the repo**
```bash
git clone https://github.com/Gunashekhar4/SQL-Powered-College-Event-Management-System.git
```

**2. Move to XAMPP's htdocs**
```bash
# Windows
cp -r SQL-Powered-College-Event-Management-System C:/xampp/htdocs/event-management

# macOS / Linux
cp -r SQL-Powered-College-Event-Management-System /opt/lampp/htdocs/event-management
```

**3. Start Apache & MySQL** from the XAMPP Control Panel

**4. Set up the database**
- Open [http://localhost/phpmyadmin](http://localhost/phpmyadmin)
- Create a new database: `event_management`
- Import the `.sql` file from the project directory

**5. Configure DB connection**

Update the database config file in the project:
```php
$host     = "localhost";
$user     = "root";
$password = "";
$database = "event_management";
```

**6. Launch the app**
```
http://localhost/event-management
```

---

## 📁 Project Structure

```
event-management/
├── admin/               # Admin dashboard & event management
├── assets/              # Images, CSS, JS files
│   ├── css/
│   ├── js/
│   └── img/
├── includes/            # DB connection, session handlers
├── user/                # User dashboard & registration
├── index.php            # Landing page
├── login.php            # Login page
├── register.php         # User registration
└── database.sql         # SQL schema & seed data
```

---

## 🧪 Test Cases

| # | Module | Test | Result |
|---|--------|------|--------|
| 1 | Auth | Login with valid credentials | ✅ Pass |
| 2 | Auth | Login with invalid credentials | ✅ Pass |
| 3 | Auth | Password recovery flow | ✅ Pass |
| 4 | Events | Create new event | ✅ Pass |
| 5 | Events | Update event details | ✅ Pass |
| 6 | Events | Delete event | ✅ Pass |

---

## 🔮 Roadmap

- [ ] Payment gateway integration for ticketed events
- [ ] Mobile application (Android / iOS)
- [ ] Email notifications on registration
- [ ] AI-based personalized event recommendations
- [ ] QR code check-in for participants
