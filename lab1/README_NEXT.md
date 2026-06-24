# Next.js (การใช้งาน)

โปรเจคนี้ได้รับการปรับให้ใช้ Next.js สำหรับ frontend (SSR/SSG/CSR) โดยมีไฟล์พื้นฐานที่เพิ่มเข้ามาเพื่อเริ่มต้นการพัฒนา

ไฟล์ที่เพิ่ม
- `package.json` — สคริปต์ `dev`, `build`, `start` และ dependencies (`next`, `react`, `react-dom`)
- `next.config.js` — คอนฟิกเริ่มต้น
- `pages/` — หน้าเริ่มต้น `pages/index.js` และ `pages/_app.js`
- `styles/globals.css` — สไตล์รวม
- `.gitignore` — ยกเว้น `node_modules` และ `.next`

คำสั่งเริ่มต้น (จากโฟลเดอร์ `lab1`):

```bash
npm install
npm run dev
```

คำสั่งสำหรับ production:

```bash
npm run build
npm start
```

หมายเหตุ
- หากต้องการเพิ่ม TypeScript, Tailwind, หรือการตั้งค่าอื่น ๆ บอกผมได้ ผมจะช่วยติดตั้งและตั้งค่าต่อให้.
