# LumaCue

<p align="center">
  <img src="https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/lumacue-icon.png" alt="LumaCue" width="132">
</p>

<p align="center">
  <strong>แอปบน Windows สำหรับรับเพลงที่คนดูขอผ่าน Twitch จัดการคิว และแสดงข้อมูลเพลงบน OBS</strong>
</p>

<p align="center">
  <a href="README.md"><strong>TH</strong></a>
  &nbsp;|&nbsp;
  <a href="README_EN.md">EN</a>
  &nbsp;|&nbsp;
  <a href="https://github.com/xyhoxx/lumacue-releases/releases/latest">ดาวน์โหลดสำหรับ Windows</a>
  &nbsp;|&nbsp;
  <a href="CHANGELOG.md">ประวัติการอัปเดต</a>
</p>

## ดาวน์โหลด

**ถ้ามีอินเทอร์เน็ต แนะนำให้ใช้ Setup Online**

1. เปิดหน้า [release ล่าสุด](https://github.com/xyhoxx/lumacue-releases/releases/latest)
2. ที่ส่วน **Assets** ดาวน์โหลด `LumaCue-Setup-Online.exe`
3. เปิดไฟล์ติดตั้ง แล้วเปิด LumaCue จาก Start Menu หรือไอคอนลัดบนเดสก์ท็อป

`LumaCue-Setup-Online.exe` มีขนาดเล็กและใช้เวลาติดตั้งน้อยกว่า เพราะตัวติดตั้งจะดาวน์โหลด LumaCue รุ่นล่าสุดระหว่างการติดตั้ง จึงต้องเชื่อมต่ออินเทอร์เน็ต

ถ้าต้องการติดตั้งโดยไม่ใช้อินเทอร์เน็ต หรืออยากเก็บตัวติดตั้งแบบครบชุดไว้ใช้ภายหลัง ให้เลือก `LumaCue-Setup-Offline-<version>.exe`

| ไฟล์ | เหมาะกับกรณีไหน | หมายเหตุ |
| --- | --- | --- |
| `LumaCue-Setup-Online.exe` | ติดตั้งบนเครื่องที่เชื่อมต่ออินเทอร์เน็ต | แนะนำสำหรับผู้ใช้ส่วนใหญ่ |
| `LumaCue-Setup-Offline-<version>.exe` | ติดตั้งโดยไม่ใช้อินเทอร์เน็ต หรือต้องการเก็บตัวติดตั้งแบบครบชุดไว้ | ดาวน์โหลดครั้งเดียวและนำไปใช้ซ้ำได้ |
| `LumaCue-win-x64-<version>.zip` | ต้องการเปิดโปรแกรมโดยไม่ผ่านขั้นตอนติดตั้ง | เหมาะกับการใช้งานแบบพกพา |
| `LumaCue-app-*`, `LumaCue-runtime-*`, `LumaCue-patch-*`, `latest.yml`, manifest | ไม่ต้องโหลดเอง | LumaCue และระบบอัปเดตจะจัดการไฟล์เหล่านี้ให้ |

## เริ่มต้นใช้งาน

1. ติดตั้ง LumaCue ด้วย Setup Online หรือใช้ตัว Offline ถ้าต้องการติดตั้งโดยไม่ใช้อินเทอร์เน็ต
2. เปิดหน้า **Twitch** แล้วเชื่อมบัญชี **Broadcaster** ถ้า LumaCue แจ้งว่าต้องขอสิทธิ์เพิ่ม ให้กด **Reconnect**
3. สร้างหรือเลือกรางวัล Channel Points ที่จะใช้รับคำขอเพลง จากนั้นกดเริ่มรับเพลง
4. เพิ่ม **Browser Source** ใน OBS ด้วย URL นี้

   ```text
   http://127.0.0.1:5000/overlay-player.html
   ```

## ทำอะไรได้บ้าง

- เปิดให้คนดูขอเพลงผ่าน Twitch Channel Points
- จัดลำดับ ลบ และดูแลคิวด้วย Global Blocklist, learned rules และ Auto DJ
- แสดงเพลงที่กำลังเล่นและเพลงในคิวบน OBS ผ่าน Browser Source โดยใช้ URL เดิมได้ทุกครั้ง
- เพิ่มเพลงจาก YouTube, YouTube Music, Spotify track/playlist และไฟล์เพลงในเครื่อง
- ควบคุมการเล่นเพลงจากแอปบน Windows และแสดงสถานะเพลงใน Discord ผ่าน Rich Presence

## สิ่งที่ต้องมี

- Windows 10 ขึ้นไป
- อินเทอร์เน็ตสำหรับ Setup Online, อัปเดตโปรแกรม และค้นหาเพลงออนไลน์
- OBS ที่รองรับ Browser Source ถ้าต้องการใช้ overlay
- สถานะ Twitch Affiliate หรือ Partner ถ้าต้องการรับเพลงผ่าน Channel Points

## ความเป็นส่วนตัวและความปลอดภัย

- ข้อมูลคิว การตั้งค่า คลัง Local Music และค่าของ overlay จะถูกเก็บและทำงานอยู่บนเครื่องของคุณ
- Twitch token จะถูกเก็บไว้ในเครื่อง โดยเข้ารหัสด้วย Windows DPAPI
- แอปไม่ได้ฝัง Twitch client secret ไว้ในไฟล์โปรแกรม ข้อมูลส่วนนี้อยู่บนเซิร์ฟเวอร์ที่ใช้สำหรับเชื่อมบัญชี

### ผลตรวจสอบความปลอดภัย

ไฟล์ที่ตรวจคือ `LumaCue.exe` ใน `LumaCue-app-win-x64-0.8.8.zip` โดยมี SHA-256:

`AE7D0B15DF7BEF79289551684694EC315A6BC083362331611A22CBE4F4BC6B4C`

[VirusTotal](https://www.virustotal.com/gui/file/ae7d0b15df7bef79289551684694ec315a6bc083362331611a22cbe4f4bc6b4c) รายงานผล `0/68` หมายความว่าไม่มีผู้ให้บริการสแกนรายใดแจ้งว่าไฟล์นี้เป็นอันตรายในตอนที่ตรวจ

![ผลสแกน VirusTotal ของ LumaCue v0.8.8](https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/security/virustotal-v0.8.8-detection.png)

ผลตรวจ [Kaspersky OpenTIP](https://opentip.kaspersky.com/78F1EF8EB881B09A91F46E4181A619F8D8504F479CAD412A8942757B86FFAA36/results) ที่มีอยู่เป็นหลักฐานของไฟล์ v0.8.6: รายงาน `0` detections และ `0` suspicious activities ส่วน network activity `1` รายการถูกจัดเป็น Good ขณะที่ไฟล์ที่แยกออกมา `2` รายการยังไม่ได้จัดหมวดหมู่ ซึ่งไม่ใช่การแจ้งเตือนมัลแวร์

![ผลวิเคราะห์ Kaspersky OpenTIP ของ LumaCue v0.8.6](https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/security/opentip-v0.8.6-dynamic-analysis.png)

ผลตรวจแต่ละส่วนใช้กับไฟล์และ hash ที่ระบุในส่วนนั้นเท่านั้น ไม่ได้ครอบคลุม installer หรือไฟล์อื่น ๆ ควรดาวน์โหลด LumaCue จากหน้า release ของ repo นี้เท่านั้น

## แก้ปัญหาเบื้องต้น

- **ควรดาวน์โหลดไฟล์ไหน?** ถ้าเครื่องเชื่อมต่ออินเทอร์เน็ต ให้ใช้ `LumaCue-Setup-Online.exe` ถ้าต้องติดตั้งแบบออฟไลน์ ให้ใช้ `LumaCue-Setup-Offline-<version>.exe`
- **Twitch ขอให้เชื่อมบัญชีใหม่?** กด **Reconnect** ในส่วน Broadcaster ได้เลย รางวัลและการตั้งค่ารับคำขอเพลงเดิมจะยังอยู่
- **สร้างรางวัล Channel Points ไม่ได้?** ช่อง Twitch ต้องมีสถานะ Affiliate หรือ Partner ก่อนจึงจะใช้ฟีเจอร์นี้ได้
- **OBS overlay ไม่แสดงข้อมูล?** ตรวจว่า LumaCue ยังเปิดอยู่ และตั้ง URL ของ Browser Source เป็น `http://127.0.0.1:5000/overlay-player.html`

## ซอร์สโค้ด

ตอนนี้ซอร์สโค้ดของ LumaCue ยังไม่ได้เปิดเป็นสาธารณะ ส่วน repo นี้เอาไว้เก็บตัวติดตั้ง ไฟล์อัปเดต changelog และคู่มือการใช้งาน

ในอนาคตอาจเปิดซอร์สโค้ดเมื่อพร้อม และจะเพิ่มเอกสารสำหรับนักพัฒนาในตอนนั้น
