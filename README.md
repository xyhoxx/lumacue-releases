# LumaCue

<p align="center">
  <img src="https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/lumacue-icon.png" alt="LumaCue" width="132">
</p>

<p align="center">
  <strong>รับเพลงจากคนดูบน Twitch จัดคิวให้ และขึ้นข้อมูลเพลงบน OBS สำหรับสตรีมเมอร์ Windows</strong>
</p>

<p align="center">
  <a href="README.md"><strong>TH</strong></a>
  &nbsp;|&nbsp;
  <a href="README_EN.md">EN</a>
  &nbsp;|&nbsp;
  <a href="https://github.com/xyhoxx/lumacue-releases/releases/latest">ดาวน์โหลดสำหรับ Windows</a>
  &nbsp;|&nbsp;
  <a href="CHANGELOG.md">อัปเดตแต่ละรุ่น</a>
</p>

## ดาวน์โหลด

**ถ้ามีอินเทอร์เน็ต ให้ใช้ Setup Online**

1. เปิดหน้า [release ล่าสุด](https://github.com/xyhoxx/lumacue-releases/releases/latest)
2. ที่ส่วน **Assets** ดาวน์โหลด `LumaCue-Setup-Online.exe`
3. รันตัวติดตั้ง แล้วเปิด LumaCue จาก Start Menu หรือ desktop shortcut

`LumaCue-Setup-Online.exe` เล็กและติดตั้งเร็วที่สุด ตัวติดตั้งจะดาวน์โหลด LumaCue รุ่นล่าสุดให้ระหว่างทาง จึงต้องต่ออินเทอร์เน็ต

ถ้าจะติดตั้งตอนออฟไลน์ หรืออยากเก็บตัวติดตั้งเต็มไว้ใช้ทีหลัง ให้เลือก `LumaCue-Setup-Offline-<version>.exe`

| ไฟล์ | ใช้เมื่อ... | สำหรับ... |
| --- | --- | --- |
| `LumaCue-Setup-Online.exe` | มีอินเทอร์เน็ตและอยากติดตั้งแบบเร็ว ๆ | ตัวเลือกแนะนำ |
| `LumaCue-Setup-Offline-<version>.exe` | จะติดตั้งตอนออฟไลน์ หรืออยากเก็บตัวติดตั้งเต็มไว้ | ติดตั้งออฟไลน์หรือใช้ซ้ำ |
| `LumaCue-win-x64-<version>.zip` | อยากเปิดใช้แบบพกพา ไม่ต้องติดตั้ง | คนที่ไม่อยากติดตั้ง |
| `LumaCue-app-*`, `LumaCue-runtime-*`, `LumaCue-patch-*`, `latest.yml`, manifest | ไม่ต้องโหลดเอง | LumaCue ใช้ตอนอัปเดต |

## เริ่มต้นใช้งาน

1. ติดตั้ง LumaCue ด้วย Setup Online หรือใช้ตัว Offline ถ้าจำเป็น
2. เปิดหน้า **Twitch** แล้วเชื่อมบัญชี **Broadcaster** ถ้า LumaCue ต้องขอสิทธิ์เพิ่ม ให้กด **Reconnect**
3. สร้างหรือเลือก Channel Points reward แล้วกดเริ่มรับเพลง
4. เพิ่ม **Browser Source** ใน OBS ด้วย URL นี้

   ```text
   http://127.0.0.1:5000/overlay-player.html
   ```

## ทำอะไรได้บ้าง

- ให้คนดูขอเพลงผ่าน Twitch Channel Points
- เรียง ลบ และคุมคิวด้วย Global Blocklist, learned rules และ Auto DJ
- ขึ้นเพลงที่กำลังเล่นและคิวบน OBS ผ่าน Browser Source URL เดิมทุกครั้ง
- รับเพลงจาก YouTube, YouTube Music, Spotify track/playlist และไฟล์เพลงในเครื่อง
- ทำงานบนเครื่อง Windows พร้อมหน้าควบคุมและ Discord Rich Presence

## สิ่งที่ต้องมี

- Windows 10 ขึ้นไป
- อินเทอร์เน็ตสำหรับ Setup Online, อัปเดตโปรแกรม และค้นหาเพลงออนไลน์
- OBS Browser Source ถ้าจะใช้ overlay
- สถานะ Twitch Affiliate หรือ Partner ถ้าจะรับเพลงผ่าน Channel Points

## ความเป็นส่วนตัวและความปลอดภัย

- คิว การตั้งค่า คลัง Local Music และ overlay ทั้งหมดทำงานบนเครื่องของคุณ
- Twitch token เก็บไว้ในเครื่องและเข้ารหัสด้วย Windows DPAPI
- ตัวโปรแกรมไม่มี Twitch client secret ข้อมูลส่วนนี้อยู่ฝั่งเซิร์ฟเวอร์ที่ใช้เชื่อมบัญชี

### ผลตรวจสอบความปลอดภัย

ไฟล์ที่ตรวจคือ `LumaCue.exe` ใน `LumaCue-app-win-x64-0.8.6.zip` โดยมี SHA-256:

`78F1EF8EB881B09A91F46E4181A619F8D8504F479CAD412A8942757B86FFAA36`

[VirusTotal](https://www.virustotal.com/gui/file/78f1ef8eb881b09a91f46e4181a619f8d8504f479cad412a8942757b86ffaa36/detection) ขึ้น `0/68` ไม่มีเอนจินใดแจ้งว่าไฟล์นี้เป็นอันตรายในตอนที่สแกน

![ผลสแกน VirusTotal ของ LumaCue v0.8.6](https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/security/virustotal-v0.8.6-detection.png)

[Kaspersky OpenTIP](https://opentip.kaspersky.com/78F1EF8EB881B09A91F46E4181A619F8D8504F479CAD412A8942757B86FFAA36/results) ขึ้น `0` detections และ `0` suspicious activities ส่วน network activity `1` รายการถูกจัดเป็น Good และไฟล์ที่แยกออกมา `2` รายการยังไม่ถูกจัดหมวดหมู่ ไม่ใช่การแจ้งเตือนมัลแวร์

![ผลวิเคราะห์ Kaspersky OpenTIP ของ LumaCue v0.8.6](https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/security/opentip-v0.8.6-dynamic-analysis.png)

ผลด้านบนเป็นของไฟล์และ hash ที่ระบุเท่านั้น ไม่ใช่ผลสแกนของ installer หรือไฟล์อื่น ดาวน์โหลด LumaCue จากหน้า release ของ repo นี้เท่านั้น

## แก้ปัญหาเบื้องต้น

- **ควรโหลดไฟล์ไหน?** ถ้ามีอินเทอร์เน็ต ใช้ `LumaCue-Setup-Online.exe` ถ้าจะติดตั้งตอนออฟไลน์ ใช้ `LumaCue-Setup-Offline-<version>.exe`
- **Twitch ขอให้เชื่อมใหม่?** กด **Reconnect** ฝั่ง Broadcaster ได้เลย reward และการตั้งค่ารับเพลงจะยังอยู่
- **สร้าง Channel Points ไม่ได้?** ช่องต้องเป็น Twitch Affiliate หรือ Partner ก่อน
- **OBS overlay ว่าง?** เช็กว่า LumaCue เปิดอยู่ และใช้ `http://127.0.0.1:5000/overlay-player.html`

## ซอร์สโค้ด

ตอนนี้ซอร์สโค้ดของ LumaCue ยังเป็น private ส่วน repo นี้เก็บตัวติดตั้ง ไฟล์อัปเดต changelog และคู่มือสำหรับคนใช้โปรแกรม

อนาคตอาจเปิดเป็น open source ถ้าพร้อม เมื่อถึงตอนนั้นค่อยเพิ่มเอกสารสำหรับนักพัฒนา
