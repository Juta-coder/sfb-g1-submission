# SFB ROI Hackathon 2026 — Gate 1 Submission Site

เว็บแอปสำหรับพนักงานกรอกข้อมูล Gate 1 (baseline, ROI, แผนดำเนินงาน 3 เดือน) ของโปรเจก SFB Hackathon 2026

**Repo นี้เป็น Private — ห้ามเปลี่ยนเป็น Public** เพราะมีข้อมูลอ่อนไหวอยู่ในไฟล์:
- `admin.html` — มีรหัส admin ฝังอยู่ในโค้ด (ใช้แก้ข้อมูลหัวหน้างาน)
- `teams/*.json` — ข้อมูลปัญหา, baseline, อีเมลหัวหน้างานของทั้ง 45 ทีม
- `index.html` — มี URL ของ Google Apps Script (endpoint ที่เขียนข้อมูลลง Google Sheet) ฝังอยู่ ถ้าหลุดออกไปคนนอกจะสามารถยิงข้อมูลปลอมเข้า Sheet ได้

## โครงสร้างไฟล์
- `index.html` — ฟอร์มที่พนักงานใช้กรอกข้อมูล (deploy บน Netlify)
- `admin.html` — หน้าสำหรับ Jutaporn แก้ไขข้อมูลหัวหน้างานของแต่ละทีม
- `teams/` — ข้อมูลรายทีม (43 ทีมจริง + 2 ทีม mock test: SFB-0000, SFB-0001)

## Deploy
Deploy ผ่าน Netlify Drop (app.netlify.com/drop) — ลากทั้งโฟลเดอร์นี้ไปวาง จะได้ลิงก์เว็บทันที
ถ้ามีการแก้ไฟล์ในนี้ (เช่นแก้ข้อมูลทีมผ่าน admin.html) ต้องลาก deploy ใหม่ทับของเดิมทุกครั้ง

## ข้อมูลจะถูกบันทึกไปที่ไหน
ทุกครั้งที่พนักงานกด submit ระบบจะ:
1. สร้าง PDF ให้โหลดลงเครื่อง (ไว้ส่งอีเมลให้หัวหน้างานรับรอง)
2. ส่งข้อมูลไปบันทึกที่ Google Sheet "Gate 1 : Project details submission" ผ่าน Google Apps Script (ดูโค้ด receiver ได้ที่ AppsScript_Code.gs — ไม่ได้เก็บไว้ใน repo นี้เพราะมีคำแนะนำการ deploy)
