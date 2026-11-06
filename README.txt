SIRIRAJ PALLIATIVE CARE — เว็บไซต์ (HTML/CSS/JS แยกไฟล์ + เนื้อหาแยกเป็นไฟล์ข้อมูล)

เปิดดูในเครื่อง: ดับเบิลคลิก index.html (ต้องต่ออินเทอร์เน็ตเพื่อโหลดฟอนต์)

โครงสร้าง
  index.html            หน้าหลัก
  pages/                about, posts, articles, article (หน้ารายละเอียดบทความ), knowledge, stories, media, contact
  data/articles.json    บทความทั้งหมด   <-- เพิ่ม/แก้บทความที่นี่ (หรือผ่านหน้า /admin)
  data/stories.json     เรื่องสั้นและหนังสือ
  data/data.js          สำเนาข้อมูลสำหรับเปิดไฟล์ในเครื่อง (สร้างด้วย tools/build-data.py)
  css/style.css         สี ฟอนต์ ขนาด ระยะห่าง
  js/components.js      เมนู + footer ทุกหน้า (แก้ที่เดียว)
  js/render.js          วางบทความ/หนังสือจากไฟล์ข้อมูลลงหน้าเว็บ + ค้นหา + แบ่งหน้า
  js/effects.js         เอฟเฟกต์, ปุ่มขนาดตัวอักษร, ดูรูปขยาย
  js/contact.js         ฟอร์มติดต่อ (ตัวอย่าง ยังไม่ส่งข้อมูลจริง)
  admin/                หน้าแก้ไขเนื้อหา (Decap CMS) — ต้องตั้งค่าก่อนใช้ ดูด้านล่าง
  fonts/  images/       ฟอนต์ และรูปทั้งหมด

เพิ่มบทความ (แบบแก้ไฟล์เอง)
  1. เปิด data/articles.json เพิ่มก้อน {...} ใหม่ในรายการ items (id ต้องเป็นอังกฤษ ไม่ซ้ำ)
  2. วางรูปปกใน images/articles/ แล้วใส่ "image": "images/articles/ชื่อไฟล์.jpg"
  3. ถ้าจะดูในเครื่องแบบดับเบิลคลิก รัน: python3 tools/build-data.py  (เว็บที่ deploy แล้วไม่ต้องรัน)
  ฟิลด์: id, title, image, excerpt (ข้อความย่อในการ์ด), body (เนื้อหาเต็ม เว้นบรรทัดว่าง = ย่อหน้าใหม่),
         date, featured (true = แสดงในหน้าหลัก)

ขึ้นเว็บ (แนวทาง A: โฮสต์สำเร็จรูป + CMS)
  ขั้น 1 ทดสอบเร็วๆ: ลากโฟลเดอร์นี้ไปวางที่ Netlify Drop ได้ลิงก์ทันที (ยังไม่มีหลังบ้าน)
  ขั้น 2 ใช้งานจริง:
    - สร้าง repo บน GitHub แล้วอัปโหลดโฟลเดอร์นี้
    - เชื่อม repo กับ Netlify / Cloudflare Pages / GitHub Pages ให้ deploy อัตโนมัติ
    - ผูกโดเมนของหน่วยงาน
    - ฟอร์มติดต่อ: ใช้ Netlify Forms หรือ Formspree แล้วแก้ js/contact.js + pages/contact.html
  ขั้น 3 หลังบ้าน (หน้า /admin): แก้ repo ใน admin/config.yml ให้ตรงกับ GitHub แล้วตั้งระบบล็อกอิน
    ของ Decap CMS (ต้องให้คนที่พอเขียนโค้ดได้ช่วยตั้งครั้งแรก) ไฟล์ตั้งค่านี้ยังไม่ได้ทดสอบกับ repo จริง
    ถ้ายังไม่ตั้ง ก็แก้ data/*.json ตรงๆ ได้

รอเนื้อหาจริง: หน้า about (บริการ 3 ช่อง), posts, knowledge, รูปปกบทความ, เบอร์/อีเมล/ที่อยู่
บทความที่ 7 (หมอ IR) ยังรอข้อความย่อ  | หน้า สื่อ ยังเป็น HTML ตรงๆ (รูปคงที่ 7 รูป)
