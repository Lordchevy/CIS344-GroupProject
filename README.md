# CIS344-GroupProject[README.md](https://github.com/user-attachments/files/23283445/README.md)
# 🧰 Equipment Rental Management System
*A PHP + MySQL web application for managing equipment rentals.*

---

## 📖 Overview
The **Equipment Rental Management System** is a web-based application that allows users to browse, rent, and manage equipment online. It simulates a real-world rental business system, handling essential operations like user registration, browsing available equipment, creating rental orders, and tracking rental history.

This project demonstrates how **PHP**, **MySQL**, **HTML**, and **CSS** can work together to create a secure and dynamic CRUD-based system. It was designed and built entirely by **Damián Chevalier** for the CIS 344 course.

---

## 🗂️ Project Structure
```
/project-root
│
├── /app
│   ├── /controllers      # Handles app logic (Auth, Equipment, Rental)
│   ├── /models           # Database models for tables
│   ├── /views            # HTML templates (forms, lists, etc.)
│
├── /public               # Web root (accessible to users)
│   ├── index.php         # Main entry point
│   ├── /css              # Stylesheets
│   ├── /js               # Scripts
│   └── /images           # Images and icons
│
├── /sql
│   ├── schema.sql        # Database structure
│   └── seed_data.sql     # Sample data for testing
│
└── /config
    └── db.php            # Database connection using PDO
```

---

## ⚙️ Features
✅ **User Registration & Login** — New users can sign up securely with password hashing.  
✅ **Equipment Catalog** — Browse equipment with category grouping and pricing.  
✅ **Rental Creation** — Select items, choose rental dates, and calculate total cost automatically.  
✅ **Admin Functions** — (Manual role assignment in DB) Add, edit, or remove equipment.  
✅ **Database Transactions** — Ensure data integrity when processing rentals.  
✅ **Security Measures** — Input validation, prepared statements, and password hashing.

---

## 🧩 Technologies Used
| Component | Technology |
|------------|-------------|
| Backend | PHP (PDO) |
| Database | MySQL |
| Frontend | HTML, CSS |
| Server | Apache (via XAMPP, WAMP, or similar) |
| Architecture | Simple MVC (Model-View-Controller) |

---

## 🧱 Database Design
The system uses a relational database with **five tables** and foreign key relationships:

- **users** – Stores user info and hashed passwords  
- **categories** – Equipment categories (e.g., Power Tools, Ladders, Generators)  
- **equipment** – Equipment details, including category and daily rate  
- **rentals** – Rental orders with start/end dates and total cost  
- **rental_items** – Links rentals to equipment with quantity and rates  

Example relationship:
```
equipment.category_id → categories.id
rental_items.rental_id → rentals.id
rentals.user_id → users.id
```

---

## 🖥️ Installation Guide

### **Step 1: Clone the repository**
```bash
git clone https://github.com/yourusername/equipment-rental-system.git
cd equipment-rental-system
```

### **Step 2: Set up the database**
1. Open **phpMyAdmin** (or MySQL CLI).
2. Create a new database:
   ```sql
   CREATE DATABASE rental;
   ```
3. Import the provided SQL files:
   - `sql/schema.sql` — Creates tables.
   - `sql/seed_data.sql` — Inserts sample data.

### **Step 3: Configure database connection**
Edit `/config/db.php` and update your credentials:
```php
$dsn = "mysql:host=127.0.0.1;dbname=rental;charset=utf8mb4";
$user = "root";
$pass = "";
```

### **Step 4: Start the local server**
If using XAMPP/WAMP/MAMP:
- Move the project folder into your `htdocs` directory.
- Start **Apache** and **MySQL**.
- Visit:  
  👉 `http://localhost/equipment-rental-system/public`

---

## 🧭 Usage Guide

### 👤 **For Regular Users**
1. Register for an account using the sign-up form.  
2. Log in using your credentials.  
3. Browse available equipment listed by category.  
4. Select equipment and specify rental start & end dates.  
5. Submit your rental order and receive a success confirmation.  

### 🛠️ **For Admins**
*(Currently, admin roles must be added manually in the database.)*
1. Log in using admin credentials.  
2. Use the inventory management section to add, update, or remove items.  
3. Monitor rental data directly in the database (future UI planned).  

---

## 🔒 Security Highlights
- **Password Hashing:** Uses `password_hash()` and `password_verify()` for secure storage.  
- **Input Validation:** `filter_var()` and `type casting` prevent malformed input.  
- **SQL Injection Protection:** All queries use **prepared statements**.  
- **Transaction Control:** Ensures rentals and rental items insertions are atomic.

Example:
```php
$stmt = $pdo->prepare("INSERT INTO users (name, email, password_hash) VALUES (?, ?, ?)");
$stmt->execute([$name, $email, password_hash($pass, PASSWORD_DEFAULT)]);
```

---

## 📷 Screenshots (Optional)
You can include images here once uploaded to GitHub:
```
![Home Page](screenshots/home.png)
![Equipment List](screenshots/equipment.png)
![Rental Form](screenshots/rental.png)
```

---

## 🚀 Future Improvements
- Responsive front-end with **Bootstrap** or **Vue.js**
- Full **admin dashboard**
- **Payment integration** (Stripe or PayPal)
- **Search and filter** options for equipment
- **Email notifications** for rental confirmations

---

## 📚 Developer Notes
This project was built independently to demonstrate:
- Full-stack development using PHP & MySQL  
- Secure backend design with PDO  
- Database normalization & foreign key relationships  
- Practical MVC pattern structure  

---

## 👨‍💻 Author
**Damián Chevalier**  
📧 [YourEmail@example.com]  
🌐 [https://github.com/yourusername](https://github.com/yourusername)
