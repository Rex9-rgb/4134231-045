# แผนงานสร้าง backend สำหรับโครงการ Lab1 (ธนาคารขยะ)

วัตถุประสงค์
- สร้าง API backend เพื่อจัดการผู้ใช้ การยืนยันตัวตน รายการขยะ และธุรกรรม (รับ/ส่ง) พร้อมฐานข้อมูลและชุดทดสอบ

ข้อเสนอเทคโนโลยี (แนะนำ)
- ภาษา: Node.js
- เฟรมเวิร์ก: Express หรือ NestJS (NestJS เหมาะกับโค้ดที่มีโครงสร้างและขยายได้)
- ฐานข้อมูล: PostgreSQL (พัฒนา: SQLite หรือ Postgres local)
- มิเกรชัน: Prisma หรือ Knex + migrations
- การทดสอบ: Jest + Supertest
- Auth: JWT (access + refresh) และ role-based access (manager/operator)

API แนะนำ (ตัวอย่าง)
- POST /api/auth/register — ลงทะเบียนผู้ใช้
- POST /api/auth/login — เข้าสู่ระบบ (คืน JWT)
- POST /api/auth/refresh — รีเฟรช token
- GET /api/users — (manager) ดึงรายชื่อผู้ใช้
- GET /api/wastes — ดึงรายการประเภทขยะ
- POST /api/wastes — สร้างประเภทขยะ (manager)
- GET /api/transactions — ดึงรายการธุรกรรม (filter ตาม user/date/status)
- POST /api/transactions — สร้างรายการรับ/ส่งขยะ
- PATCH /api/transactions/:id/status — อัปเดตสถานะ (operator/manager)

โมเดลข้อมูล (ย่อ)
- User: id, name, email, password_hash, role
- WasteType: id, name, unit
- Transaction: id, user_id, waste_type_id, quantity, status, created_at, updated_at

งานย่อยและลำดับการทำ
1. สร้าง repo/โฟลเดอร์ backend: `lab1/src/backend` พร้อม `package.json` และ `README.md`
2. ตั้งค่า ORM (Prisma) + schema และมิเกรชันเริ่มต้น
3. สร้างระบบ auth (register/login/jwt)
4. สร้าง endpoints สำหรับ `wastes` และ `transactions`
5. เขียน validation (Joi/Zod) และ error handling กลาง
6. เขียนชุดทดสอบหน่วยและอินทิเกรชัน (Jest + Supertest)
7. เพิ่มสคริปต์ `npm run dev`, `npm run test`, `npm run migrate` และเอกสารการรัน
8. ตั้งค่า basic CI (GitHub Actions) สำหรับรันเทสต์และมิเกรชัน

คำสั่งตัวอย่าง (เมื่อ scaffold เสร็จ)

```bash
cd lab1/src/backend
npm install
npm run dev
```

ประเมินเวลา (คร่าว ๆ)
- Scaffold + ORM + auth basic: 1-2 วัน
- CRUD endpoints + validation: 1-2 วัน
- Tests + CI: 1-2 วัน

ถัดไปที่ผมทำให้ได้ทันที
- สร้างโครงสร้าง `lab1/src/backend` พร้อม `package.json`, โฟลเดอร์ `src`, และตัวอย่างไฟล์ entry (server.js / main.ts)

ให้บอกผมว่าต้องการ
- เลือกเฟรมเวิร์ก: `express` หรือ `nest` หรือ `django`
- ใช้ ORM ใด: `prisma` หรือ `knex` หรือ `typeorm`
- ต้องการให้ผม scaffold โค้ดเริ่มต้นเลยหรือแค่เตรียม `task.md` เท่านั้น
