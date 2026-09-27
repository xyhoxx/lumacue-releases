# LumaCue

[ไทย](README.md) | [English](README_EN.md)

LumaCue เป็นแอปเล่นเพลงสำหรับสตรีมบน Windows 10 ขึ้นไป คนดูขอเพลงผ่าน Twitch ได้ ส่วนคุณจัดคิว เปิด Auto DJ และเอาชื่อเพลงที่กำลังเล่นไปขึ้นใน OBS ได้จากแอปเดียว

**เริ่มใช้:** [ดาวน์โหลด Setup Online](https://github.com/xyhoxx/lumacue-releases/releases/latest/download/LumaCue-Setup-Online.exe) (ต้องมีอินเทอร์เน็ต) หรือ [ดูไฟล์ทั้งหมดในรุ่นล่าสุด](https://github.com/xyhoxx/lumacue-releases/releases/latest)

## เลือกไฟล์ดาวน์โหลด

- **ติดตั้งตามปกติ:** `LumaCue-Setup-Online.exe` ไฟล์เล็ก ดาวน์โหลดโปรแกรมระหว่างติดตั้ง
- **ติดตั้งตอนไม่มีเน็ต:** `LumaCue-Setup-Offline-<version>.exe` มีไฟล์ที่ต้องใช้ครบ เก็บไว้ติดตั้งทีหลังได้
- **ไม่อยากติดตั้ง:** `LumaCue-win-x64-<version>.zip` แตก ZIP แล้วเปิดใช้งานแบบพกพา

ไฟล์ `LumaCue-app-*`, `LumaCue-runtime-*`, `LumaCue-patch-*`, `latest.yml` และ manifest มีไว้ให้ระบบอัปเดต ไม่ต้องโหลดเอง

## ตั้งค่าเพื่อสตรีม

1. เปิด LumaCue แล้วเพิ่มเพลงจากช่องค้นหา ลิงก์ YouTube หรือ YouTube Music เพลงหรือเพลย์ลิสต์ Spotify และไฟล์เพลงในเครื่อง
2. ถ้าจะให้คนดูขอเพลง เปิดหน้า **Twitch** เชื่อมบัญชี **Broadcaster** เลือกรางวัล Channel Points แล้วเริ่มรับคำขอ ช่อง Twitch ต้องเป็น Affiliate หรือ Partner จึงจะใช้รางวัลแบบนี้ได้
3. ถ้าจะให้ OBS แสดงเพลง เพิ่ม **Browser Source** แล้วใส่ URL นี้ โดยเปิด LumaCue ทิ้งไว้ระหว่างสตรีม:

   ```text
   http://127.0.0.1:5000/overlay-player.html
   ```

ใช้เป็นเครื่องเล่นเพลงอย่างเดียวก็ได้ ไม่จำเป็นต้องเชื่อม Twitch หรือ OBS

การค้นหาเพลงออนไลน์และอัปเดตโปรแกรมต้องใช้อินเทอร์เน็ต

## ระหว่างสตรีม

- ย้ายหรือลบเพลงในคิว และตั้ง Blocklist สำหรับเพลงหรือศิลปินที่ไม่ต้องการ
- เปิด Auto DJ ให้ช่วยเติมคิวเมื่อเพลงเริ่มหมด โดยไม่แทนที่เพลงที่คนดูขอ
- แสดงเพลงที่กำลังเล่นและคิวบน OBS; URL ของ Browser Source ไม่ต้องเปลี่ยนเมื่อเพลงเปลี่ยน
- แสดงสถานะเพลงใน Discord ผ่าน Rich Presence

## ข้อมูลและความปลอดภัย

คิวเพลง การตั้งค่า เพลงที่นำเข้าจากเครื่อง และค่าของ overlay เก็บอยู่บนเครื่องของคุณ Twitch token ก็เก็บในเครื่องและป้องกันด้วย Windows DPAPI ส่วน Twitch client secret ไม่ได้อยู่ในไฟล์แอป แต่เก็บไว้ฝั่งบริการเชื่อมบัญชี

ถ้าโปรแกรมป้องกันไวรัสแจ้งเตือน อย่าเพิ่งปิดระบบป้องกันหรือเพิ่ม exclusion ให้ตรวจชื่อไฟล์และแหล่งดาวน์โหลดก่อน ผลสแกนด้านล่างเป็นของไฟล์ **v0.8.11 เท่านั้น** ไม่ใช่ผลรับรองรุ่นล่าสุดหรือตัวติดตั้งทุกไฟล์

<details>
<summary>ดูผลสแกน LumaCue.exe รุ่น 0.8.11</summary>

ไฟล์ `LumaCue.exe` ใน `LumaCue-app-win-x64-0.8.11.zip` มี SHA-256:

`B49A5EE1AF577CA78836B1DB6B5022344B69E3194EF6BE0AE1719EBBE297AA13`

[VirusTotal](https://www.virustotal.com/gui/file/b49a5ee1af577ca78836b1db6b5022344b69e3194ef6be0ae1719ebbe297aa13) แสดงผล `0/69` ณ เวลาที่ตรวจ หมายถึงไม่มีผู้ให้บริการสแกนรายใดแจ้งว่าไฟล์ hash นี้เป็นอันตรายในครั้งนั้น

![ผลสแกน VirusTotal ของ LumaCue v0.8.11](https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/security/virustotal-v0.8.11-detection.png)

[Kaspersky OpenTIP](https://opentip.kaspersky.com/B49A5EE1AF577CA78836B1DB6B5022344B69E3194EF6BE0AE1719EBBE297AA13/results) รายงาน `0` detections และ `0` suspicious activities สำหรับ hash เดียวกันในการตรวจครั้งนั้น

![ผลวิเคราะห์ Kaspersky OpenTIP ของ LumaCue v0.8.11](https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/security/opentip-v0.8.11-dynamic-analysis.png)

</details>

## ถ้าใช้งานติดขัด

- **Twitch ขอสิทธิ์เพิ่ม:** กด **Reconnect** ที่บัญชี Broadcaster ไม่ต้องลบรางวัลหรือตั้งค่าใหม่
- **สร้างรางวัล Channel Points ไม่ได้:** ตรวจว่าช่องเป็น Twitch Affiliate หรือ Partner
- **OBS ไม่ขึ้นเพลง:** เปิด LumaCue ไว้ และตรวจ URL ของ Browser Source ให้ตรงกับด้านบน

[ดูว่าแต่ละรุ่นเปลี่ยนอะไรบ้าง](CHANGELOG.md)

ซอร์สโค้ดยังไม่ได้เปิดเป็นสาธารณะ repo นี้ใช้แจกตัวติดตั้งและไฟล์อัปเดต หากเปิดซอร์สโค้ดในอนาคตจะเพิ่มข้อมูลไว้ที่นี่
