# mysql<div align="center">

# 🐬 Ultimate MySQL Cheat Sheet

**Database Management · Querying · Users · Functions · Optimization**  
_Every essential MySQL command, tailored for daily use_

[![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://dev.mysql.com/doc/)
[![Version](https://img.shields.io/badge/8.0+-blue?style=for-the-badge)](https://dev.mysql.com/doc/refman/8.0/en/)

</div>

---

## 🧱 1. Database & Table Management

<div align="center">

| Command | Description |
|---------|-------------|
| `CREATE DATABASE dbname;` | নতুন ডাটাবেজ তৈরি |
| `DROP DATABASE dbname;` | ডাটাবেজ মুছে ফেলা |
| `USE dbname;` | ডাটাবেজ নির্বাচন |
| `CREATE TABLE users (id INT PRIMARY KEY AUTO_INCREMENT, name VARCHAR(50));` | টেবিল তৈরি |
| `DESCRIBE users;` | টেবিলের গঠন দেখানো |
| `ALTER TABLE users ADD email VARCHAR(100);` | নতুন কলাম যোগ |
| `ALTER TABLE users DROP COLUMN email;` | কলাম বাদ |
| `ALTER TABLE users MODIFY name VARCHAR(100);` | কলাম পরিবর্তন |
| `DROP TABLE users;` | টেবিল মুছা |
| `TRUNCATE TABLE users;` | সব রেকর্ড দ্রুত মুছা |

</div>

---

## 📝 2. Insert, Update, Delete (DML)

<div align="center">

| Command | Description |
|---------|-------------|
| `INSERT INTO users (name, age) VALUES ('Rahim', 25);` | একক রেকর্ড |
| `INSERT INTO users (name, age) VALUES ('Karim',30), ('Mina',22);` | একাধিক রেকর্ড |
| `UPDATE users SET age = 26 WHERE id = 1;` | রেকর্ড আপডেট |
| `DELETE FROM users WHERE id = 1;` | রেকর্ড মুছা |

</div>

---

## 🔍 3. Querying (DQL)

<div align="center">

| Command | Description |
|---------|-------------|
| `SELECT * FROM users;` | সব কলাম |
| `SELECT name, age FROM users;` | নির্দিষ্ট কলাম |
| `SELECT DISTINCT city FROM users;` | ডুপ্লিকেট বাদ |
| `SELECT * FROM users WHERE age > 25;` | শর্ত |
| `SELECT * FROM users WHERE name LIKE 'A%';` | প্যাটার্ন (`%` যেকোনো, `_` এক অক্ষর) |
| `SELECT * FROM users WHERE age BETWEEN 20 AND 30;` | রেঞ্জ |
| `SELECT * FROM users WHERE id IN (1,2,3);` | নির্দিষ্ট মান |
| `SELECT * FROM users WHERE email IS NULL;` | নাল চেক |
| `SELECT * FROM users ORDER BY age DESC;` | সাজানো |
| `SELECT * FROM users LIMIT 5 OFFSET 10;` | সীমা + পৃষ্ঠা |

</div>

---

## 🔗 4. Joins

<div align="center">

| Command | Description |
|---------|-------------|
| `INNER JOIN orders ON users.id = orders.user_id` | উভয় টেবিলে মিল |
| `LEFT JOIN orders ON users.id = orders.user_id` | বাম টেবিলের সব |
| `RIGHT JOIN orders ON users.id = orders.user_id` | ডান টেবিলের সব |
| `CROSS JOIN` | কার্টেসিয়ান প্রোডাক্ট |

</div>

---

## 🧮 5. Aggregate Functions

<div align="center">

| Function | Description |
|----------|-------------|
| `COUNT(*)` | রেকর্ড সংখ্যা |
| `SUM(salary)` | যোগফল |
| `AVG(age)` | গড় |
| `MIN(price)`, `MAX(price)` | সর্বনিম্ন/সর্বোচ্চ |
| `GROUP BY city` | গ্রুপিং |
| `HAVING COUNT(*) > 3` | গ্রুপ ফিল্টার |

</div>

---

## 🏷️ 6. Data Types (Important MySQL Types)

<div align="center">

| Category | Types |
|----------|-------|
| **Integer** | `TINYINT`, `SMALLINT`, `INT`, `BIGINT` |
| **Decimal** | `DECIMAL(10,2)`, `FLOAT`, `DOUBLE` |
| **String** | `CHAR(10)`, `VARCHAR(100)`, `TEXT` |
| **Date/Time** | `DATE`, `DATETIME`, `TIMESTAMP`, `TIME` |
| **Binary** | `BLOB`, `LONGBLOB` |
| **Boolean** | `TINYINT(1)` |

</div>

---

## 🔐 7. User & Privileges

<div align="center">

| Command | Description |
|---------|-------------|
| `CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';` | নতুন ইউজার |
| `GRANT ALL PRIVILEGES ON dbname.* TO 'username'@'localhost';` | সব অধিকার |
| `GRANT SELECT, INSERT ON dbname.* TO 'username'@'localhost';` | নির্দিষ্ট অধিকার |
| `FLUSH PRIVILEGES;` | রিফ্রেশ |
| `REVOKE ALL PRIVILEGES ON dbname.* FROM 'username'@'localhost';` | অধিকার সরান |
| `DROP USER 'username'@'localhost';` | ইউজার মুছা |
| `SHOW GRANTS FOR 'username'@'localhost';` | অধিকার দেখুন |

</div>

---

## 🔑 8. Indexes & Constraints

<div align="center">

| Command | Description |
|---------|-------------|
| `PRIMARY KEY` | ইউনিক কী |
| `FOREIGN KEY (user_id) REFERENCES users(id)` | ফরেন কী |
| `UNIQUE` | ডুপ্লিকেট নিষেধ |
| `NOT NULL` | খালি নয় |
| `CHECK (age >= 18)` | শর্ত |
| `CREATE INDEX idx_name ON users(name);` | সাধারণ ইনডেক্স |
| `CREATE UNIQUE INDEX idx_email ON users(email);` | ইউনিক ইনডেক্স |
| `DROP INDEX idx_name ON users;` | ইনডেক্স মুছা |

</div>

---

## 🧰 9. Useful MySQL Functions

<div align="center">

| Category | Functions |
|----------|-----------|
| **String** | `CONCAT()`, `UPPER()`, `LOWER()`, `SUBSTRING()`, `LENGTH()`, `TRIM()`, `REPLACE()` |
| **Date** | `NOW()`, `CURDATE()`, `DATE_FORMAT(date, '%Y-%m-%d')`, `DATEDIFF(end, start)` |
| **Math** | `ROUND()`, `FLOOR()`, `CEIL()`, `ABS()` |
| **Control** | `IF(condition, val1, val2)`, `IFNULL(val, default)` |
| **Aggregate** | `COUNT()`, `SUM()`, `AVG()`, `MIN()`, `MAX()` |

</div>

---

## ⚡ 10. Performance & Maintenance

<div align="center">

| Command | Description |
|---------|-------------|
| `EXPLAIN SELECT * FROM users WHERE id = 1;` | কুয়েরি প্ল্যান দেখুন |
| `SHOW INDEX FROM users;` | ইনডেক্স তালিকা |
| `ANALYZE TABLE users;` | টেবিল অপটিমাইজ |
| `OPTIMIZE TABLE users;` | স্পেস রিক্লেম |
| `SHOW PROCESSLIST;` | চলমান কুয়েরি |
| `KILL process_id;` | একটি কুয়েরি বন্ধ করুন |

</div>

---

<div align="center">

### 🐬 From schema to query — everything MySQL, right here!  
**Happy Querying!**

[![Profile Views](https://komarev.com/ghpvc/?username=your-username&color=4479A1&style=flat-square)](https://github.com/your-username)

</div>
