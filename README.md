# คำศัพท์จีน HSK 1–2 (PWA)

เว็บตารางคำศัพท์ภาษาจีน HSK 1–2 (281 คำ) พร้อมพินอิน คำอ่านไทย คำแปล หมวดคำ
ฟิลเตอร์ระดับ HSK และปุ่มออกเสียงภาษาจีน (Web Speech API)

เป็น **PWA** — ติดตั้งลงเครื่อง (โทรศัพท์/คอม) และใช้งานออฟไลน์ได้หลังเปิดครั้งแรก
เป็นเว็บ static ล้วน ไม่ต้องใช้เซิร์ฟเวอร์หรือ build step

## โครงสร้าง

```
.
├── index.html              # ตัวเว็บ
├── manifest.webmanifest    # ข้อมูลแอป (ชื่อ, ไอคอน, สี, display)
├── sw.js                   # service worker (cache ไว้ใช้ออฟไลน์)
├── icons/                  # ไอคอนแอป 192 / 512 / maskable / apple-touch
├── .nojekyll               # บอก GitHub Pages ไม่ต้องประมวลผลด้วย Jekyll
└── README.md
```

> ทุก path ในโค้ดเป็นแบบ **relative** จึงทำงานได้ทั้งบน root และ subpath
> (`https://<user>.github.io/<repo>/`) ของ GitHub Pages

## เปิดดูในเครื่อง

```bash
npx serve .        # แล้วเปิด URL ที่ขึ้น (เช่น http://localhost:3000)
```

> service worker ต้องรันบน `localhost` หรือ HTTPS (GitHub Pages เป็น HTTPS อยู่แล้ว)
> ปุ่มออกเสียงต้องใช้เบราว์เซอร์ที่รองรับ Web Speech API (Chrome/Edge ดีที่สุด)
> และมีเสียงภาษาจีนติดตั้งในระบบ

## Deploy ขึ้น GitHub Pages

1. push โค้ดขึ้น GitHub (branch `main`)
2. ไปที่ **Settings → Pages** ของ repo
3. ตั้ง **Source = Deploy from a branch**, **Branch = `main` / `(root)`** แล้ว Save
4. รอสักครู่ เว็บจะอยู่ที่ `https://<username>.github.io/<repo>/`

## อัปเดตเนื้อหา

แก้ array `vocab` ใน `index.html` ได้เลย และเมื่อแก้ไฟล์ที่ถูก cache (เช่น `index.html`,
ไอคอน) ให้เพิ่มเลขเวอร์ชันใน `sw.js` (`const CACHE = 'hsk-vocab-v2'`) เพื่อบังคับให้
เครื่องผู้ใช้โหลดของใหม่
