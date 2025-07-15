
# 🎯 Smart Attendance System

An automated, secure, and scalable **Smart Attendance System** using **RFID** and **Fingerprint authentication**, built on a **Raspberry Pi**. This system not only marks attendance with timestamps but also notifies students via **Gmail** and auto-sends **absent alerts** after a cutoff time (4:00 PM).

## 📌 Features

- 🔐 **Two-Factor Authentication**: Combines RFID and fingerprint for secure identity verification.
- 🕓 **Real-time Attendance Logging**: Records exact time and date of login.
- 📧 **Automated Email Notifications**:
  - ✅ Present: Sent immediately upon fingerprint verification.
  - ❌ Absent: Automatically sent at 4:00 PM to those who haven’t checked in.
- 🗃️ **SQLite Database Integration**:
  - Stores student details, attendance status, and timestamps.
  - History tracking of daily attendance.

## 🧰 Hardware & Tools Used

- Raspberry Pi 4B
- RC522 RFID Reader
- R305 Fingerprint Sensor
- OLED Display (optional for visual feedback)
- Python 3.x
- SQLite3
- Gmail API for sending emails (OAuth2 based)

## 🧠 How It Works

1. Student scans RFID card.
2. If matched, prompted for fingerprint scan.
3. If fingerprint is verified:
   - Attendance marked in the database with date & time.
   - A “Present” confirmation email is sent.
4. At 4:00 PM:
   - Any student not marked as present is automatically recorded as “Absent”.
   - An “Absent” email is sent to them.

## 🗄️ Database Structure

### `students` Table
| id | name      | rfid_uid   | fingerprint_id | email              |
|----|-----------|------------|----------------|---------------------|
| 1  | John Doe  | 1234567890 | 3              | john@example.com    |

### `attendance` Table
| id | student_id | date       | time     | status  |
|----|------------|------------|----------|---------|
| 1  | 1          | 2025-05-14 | 10:32:55 | Present |

## 📦 Setup Instructions

```bash
git clone https://github.com/your-username/smart-attendance-system.git
cd smart-attendance-system
python3 -m venv smart-attendance-env
source smart-attendance-env/bin/activate
pip install -r requirements.txt
```

- Replace Gmail credentials in `credentials.json` and run once to generate `token.json`.
- Connect hardware as per pins and run:

```bash
python3 attendance_system.py
```

## 🛡️ Security

- Uses **Google OAuth2** for email access (no password stored).
- Fingerprint data stored securely on sensor, not in the database.

## 👨‍💻 Developed By

**Pranay**  
ECE | VBIT Hyderabad  
Passionate about Embedded Systems & IoT

## 🌟 Contributions

Feel free to fork this repository, open issues or send PRs to improve features, code, or UI. Let’s build smarter campuses!

## 📄 License

This project is licensed under the [MIT License](LICENSE).

