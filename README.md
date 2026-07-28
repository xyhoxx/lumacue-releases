# LumaCue

<p align="center">
  <img src="https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/lumacue-icon.png" alt="LumaCue" width="132">
</p>

<p align="center">
  <strong>ระบบรับขอเพลงสำหรับ Twitch, จัดการคิว, Auto DJ และ OBS music overlay สำหรับสตรีมเมอร์บน Windows</strong>
</p>

<p align="center">
  <a href="README.md"><strong>TH</strong></a>
  &nbsp;|&nbsp;
  <a href="README_EN.md">EN</a>
  &nbsp;|&nbsp;
  <a href="https://github.com/xyhoxx/lumacue-releases/releases/latest">ดาวน์โหลดสำหรับ Windows</a>
  &nbsp;|&nbsp;
  <a href="CHANGELOG.md">บันทึกการเปลี่ยนแปลง</a>
</p>

## ดาวน์โหลด

**แนะนำสำหรับผู้ใช้ทั่วไป: Setup Online**

1. เปิดหน้า [release ล่าสุด](https://github.com/xyhoxx/lumacue-releases/releases/latest)
2. ที่ส่วน **Assets** ดาวน์โหลด `LumaCue-Setup-Online.exe`
3. รันตัวติดตั้ง แล้วเปิด LumaCue จาก Start Menu หรือ desktop shortcut

`LumaCue-Setup-Online.exe` เป็นตัวติดตั้งขนาดเล็กและเร็วที่สุด โดยจะดาวน์โหลดโปรแกรมเวอร์ชันปัจจุบันระหว่างติดตั้ง จึงต้องใช้อินเทอร์เน็ต

ใช้ `LumaCue-Setup-Offline-<version>.exe` เมื่ออยากเก็บตัวติดตั้งเต็มไว้สำหรับเครื่องที่ไม่มีอินเทอร์เน็ตตอนติดตั้ง

| ไฟล์ | ใช้เมื่อ... | สำหรับ... |
| --- | --- | --- |
| `LumaCue-Setup-Online.exe` | มีอินเทอร์เน็ตและต้องการติดตั้งให้เร็วที่สุด | แนะนำสำหรับผู้ใช้ทั่วไป |
| `LumaCue-Setup-Offline-<version>.exe` | เครื่องไม่มีอินเทอร์เน็ตตอนติดตั้ง หรือต้องการเก็บตัวติดตั้งเต็มไว้ | ติดตั้งแบบออฟไลน์หรือเก็บไว้ใช้ซ้ำ |
| `LumaCue-win-x64-<version>.zip` | ต้องการใช้ LumaCue แบบพกพาโดยไม่ติดตั้ง | คนที่ไม่ต้องการติดตั้ง |
| `LumaCue-app-*`, `LumaCue-runtime-*`, `LumaCue-patch-*`, `latest.yml`, manifest | ไม่ต้องใช้สำหรับการติดตั้งปกติ | โปรแกรมอัปเดตจัดการให้อัตโนมัติ |

## เริ่มต้นใช้งาน

1. **ติดตั้ง LumaCue** ด้วย Setup Online หรือใช้ตัว Offline เมื่อจำเป็น
2. เปิดหน้า **Twitch** ใน LumaCue แล้วเชื่อมต่อบัญชี **Broadcaster** หากโปรแกรมต้องขอสิทธิ์ Twitch เพิ่ม ให้กด **Reconnect**
3. สร้างหรือเลือก Channel Points reward แล้วเริ่มรับคำขอเพลง
4. เพิ่ม OBS **Browser Source** ด้วย URL นี้

   ```text
   http://127.0.0.1:5000/overlay-player.html
   ```

## LumaCue ทำอะไรได้บ้าง

- ให้ผู้ชมขอเพลงผ่าน Twitch Channel Points
- คุมคิวด้วย queue controls, Global Blocklist, learned rules และ Auto DJ
- แสดง Now Playing และคิวบน OBS ผ่าน Browser Source URL ที่คงที่
- เพิ่มเพลงจาก YouTube, YouTube Music, Spotify track/playlist และไฟล์เพลงในเครื่อง
- ทำงานบน Windows ในเครื่อง พร้อมหน้าควบคุมและ Discord Rich Presence

## สิ่งที่ต้องมี

- Windows 10 ขึ้นไป
- อินเทอร์เน็ตสำหรับ Setup Online, การอัปเดต และค้นหาเพลงออนไลน์
- OBS Browser Source สำหรับ overlay
- Twitch Affiliate หรือ Partner หากต้องการใช้ Channel Points Custom Rewards

## ความเป็นส่วนตัวและความปลอดภัย

- คิวเพลง, การตั้งค่า, Local Music และบริการ overlay ทำงานบนเครื่องของคุณ
- Twitch token ถูกเก็บในเครื่องและป้องกันด้วย Windows DPAPI
- โปรแกรมเดสก์ท็อปไม่มี Twitch client secret; ระบบเชื่อมต่อเก็บ secret ไว้ฝั่งเซิร์ฟเวอร์

### ผลตรวจสอบความปลอดภัย

LumaCue `v0.8.4` ได้รับผล **Clean** จาก [Kaspersky OpenTIP](https://opentip.kaspersky.com/7CBF8A288F6673CA955F7591571A6C85376ECECF63B628520A1F968C5EA89165/results) สำหรับไฟล์ `LumaCue.exe` ภายในแพ็กเกจ `LumaCue-app-win-x64-0.8.4.zip` ที่มี SHA-256:

`7CBF8A288F6673CA955F7591571A6C85376ECECF63B628520A1F968C5EA89165`

การวิเคราะห์แบบ dynamic รายงาน `0` detections, `0` suspicious activities และ network activity `1` รายการที่จัดเป็น **Good**. พบ extracted files `2` รายการ ซึ่งเป็นไฟล์ที่แยกออกมาเพื่อการวิเคราะห์ ไม่ใช่การตรวจพบภัยคุกคาม

![ผลการวิเคราะห์ Kaspersky OpenTIP ของ LumaCue v0.8.4](https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/security/opentip-v0.8.4-dynamic-analysis.png)

VirusTotal สแกนไฟล์ hash เดียวกันด้วยเอนจินความปลอดภัย 69 ราย และ **ไม่มีรายใดตรวจพบว่าเป็นอันตราย (`0/69`)** ณ เวลาที่สแกน ([ดูผลสแกน](https://www.virustotal.com/gui/file/7cbf8a288f6673ca955f7591571a6c85376ececf63b628520a1f968c5ea89165/detection))

![ผลการตรวจ VirusTotal ของ LumaCue v0.8.4](https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/security/virustotal-v0.8.4-detection.png)

ผลนี้ครอบคลุมเฉพาะไฟล์และ hash ข้างต้นเท่านั้น โปรดดาวน์โหลดตัวติดตั้งจากหน้า release อย่างเป็นทางการเสมอ

## แก้ปัญหาเบื้องต้น

- **เลือกไฟล์ไหน?** ถ้ามีอินเทอร์เน็ต ให้ใช้ `LumaCue-Setup-Online.exe`; หากต้องติดตั้งแบบไม่มีอินเทอร์เน็ต ให้ใช้ `LumaCue-Setup-Offline-<version>.exe`
- **Twitch ให้เชื่อมใหม่?** กด **Reconnect** ฝั่ง Broadcaster เพื่อขอสิทธิ์ใหม่โดยไม่ล้าง reward หรือการรับคำขอเพลง
- **สร้าง Channel Points ไม่ได้?** ช่องต้องเป็น Twitch Affiliate หรือ Partner
- **OBS overlay ว่าง?** ตรวจว่า LumaCue เปิดอยู่ และใช้ `http://127.0.0.1:5000/overlay-player.html`

## ซอร์สโค้ด

ซอร์สโค้ดของ LumaCue ยังเป็น private ระหว่างที่โปรแกรมกำลังพัฒนาต่อ หน้า public นี้เก็บเฉพาะตัวติดตั้ง, ไฟล์อัปเดต, บันทึกการเปลี่ยนแปลง และคู่มือเริ่มต้นใช้งาน

ในอนาคตอาจพิจารณาเปิดเป็น open source เมื่อพร้อม เมื่อตัดสินใจเปิดแล้วจึงจะเพิ่มเอกสารและคู่มือสำหรับนักพัฒนา
