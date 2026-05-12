# Factory Stock Login + Password System

ไฟล์ในชุดนี้มี 2 ส่วน:

1. `index.html`
   - หน้าเว็บ Login
   - Admin เปลี่ยน password ตัวเองได้
   - Admin reset password ร้านค้าได้
   - ร้านค้าเปลี่ยน password ตัวเองได้

2. `Code.gs`
   - โค้ด Google Apps Script
   - ใช้เป็น backend สำหรับ login และ password management
   - เก็บข้อมูล user ใน Google Sheets แท็บ `Users`

## วิธีติดตั้ง

### 1. Google Sheets

สร้าง Google Sheet ใหม่ แล้วไปที่:

Extensions → Apps Script

ลบโค้ดเดิม แล้ววางโค้ดจากไฟล์ `Code.gs`

Deploy → New deployment → Web app

ตั้งค่า:

- Execute as: Me
- Who has access: Anyone

จากนั้น copy Web App URL ที่ลงท้ายด้วย `/exec`

### 2. แก้ index.html

หา:

```javascript
const API_URL = "PASTE_YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL_HERE";
```

เปลี่ยนเป็น:

```javascript
const API_URL = "https://script.google.com/macros/s/xxxxxxx/exec";
```

### 3. อัปโหลดขึ้น GitHub

เอา `index.html` ไปแทนไฟล์เดิมใน repo

### 4. Login เริ่มต้น

Admin:

```text
username: admin
password: admin123
```

ร้านค้า:

```text
username: C001
password: pw001
```

```text
username: C002
password: pw002
```

## หมายเหตุ

ระบบนี้ใช้ Google Sheets เป็น user database และ Apps Script เป็น backend แบบง่าย
เหมาะกับ SME และระบบทดลองใช้งานจริงระดับเริ่มต้น
