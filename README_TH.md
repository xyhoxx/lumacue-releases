# LumaCue

<p align="center">
  <img src="https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/lumacue-icon.png" alt="LumaCue" width="132">
</p>

<p align="center">
  <strong>ระบบรับขอเพลงสำหรับ Twitch, จัดการคิว, Auto DJ และ OBS music overlay สำหรับสตรีมเมอร์บน Windows</strong>
</p>

<p align="center">
  <a href="README.md">EN</a>
  &nbsp;|&nbsp;
  <a href="README_TH.md"><strong>TH</strong></a>
  &nbsp;|&nbsp;
  <a href="https://github.com/xyhoxx/lumacue-releases/releases/latest">ดาวน์โหลดสำหรับ Windows</a>
  &nbsp;|&nbsp;
  <a href="CHANGELOG_TH.md">บันทึกการเปลี่ยนแปลง</a>
</p>

## ดาวน์โหลด

**แนะนำสำหรับผู้ใช้ทั่วไป**

1. เปิดหน้า [release ล่าสุด](https://github.com/xyhoxx/lumacue-releases/releases/latest)
2. ที่ส่วน **Assets** ดาวน์โหลด `LumaCue-Setup-Offline-<version>.exe`
3. รันตัวติดตั้ง แล้วเปิด LumaCue จาก Start Menu หรือ desktop shortcut

`LumaCue-Setup-Offline-<version>.exe` มีทั้งโปรแกรมและไฟล์ที่จำเป็นต่อการทำงานอยู่แล้ว ไม่ต้องโหลด ZIP, patch, runtime, `latest.yml` หรือ manifest ด้วยตัวเอง

| ไฟล์ | ใช้เมื่อ... | สำหรับ... |
| --- | --- | --- |
| `LumaCue-Setup-Offline-<version>.exe` | ต้องการติดตั้ง LumaCue ตามปกติ | ผู้ใช้ทั่วไปและการติดตั้งครั้งแรก |
| `LumaCue-win-x64-<version>.zip` | ต้องการ full portable package โดยเฉพาะ | ผู้ใช้ขั้นสูงเท่านั้น |
| `LumaCue-app-*`, `LumaCue-runtime-*`, `LumaCue-patch-*`, `latest.yml`, manifest | ไม่ต้องใช้สำหรับการติดตั้งปกติ | โปรแกรมอัปเดตจัดการให้อัตโนมัติ |

## เริ่มต้นใช้งาน

1. **ติดตั้ง LumaCue** ด้วย offline installer
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
- อินเทอร์เน็ตสำหรับติดตั้ง อัปเดต และค้นหาเพลงออนไลน์
- OBS Browser Source สำหรับ overlay
- Twitch Affiliate หรือ Partner หากต้องการใช้ Channel Points Custom Rewards

## ความเป็นส่วนตัวและความปลอดภัย

- คิวเพลง, การตั้งค่า, Local Music และบริการ overlay ทำงานบนเครื่องของคุณ
- Twitch token ถูกเก็บในเครื่องและป้องกันด้วย Windows DPAPI
- โปรแกรมเดสก์ท็อปไม่มี Twitch client secret; การเชื่อมต่อ Twitch ใช้ Cloudflare Worker เก็บ secret ฝั่งเซิร์ฟเวอร์

## แก้ปัญหาเบื้องต้น

- **เลือกไฟล์ไหน?** ใช้ `LumaCue-Setup-Offline-<version>.exe`
- **Twitch ให้เชื่อมใหม่?** กด **Reconnect** ฝั่ง Broadcaster เพื่อขอสิทธิ์ใหม่โดยไม่ล้าง reward หรือการรับคำขอเพลง
- **สร้าง Channel Points ไม่ได้?** ช่องต้องเป็น Twitch Affiliate หรือ Partner
- **OBS overlay ว่าง?** ตรวจว่า LumaCue เปิดอยู่ และใช้ `http://127.0.0.1:5000/overlay-player.html`

## สำหรับผู้พัฒนาและผู้ดูแลระบบ

หน้า public [release repository](https://github.com/xyhoxx/lumacue-releases) เก็บตัวติดตั้ง, ไฟล์อัปเดต และเอกสาร release ส่วน source code ถูกดูแลแยกต่างหาก เนื้อหาสำหรับนักพัฒนาใน [README ภาษาอังกฤษ](README.md) ไม่ใช่ขั้นตอนติดตั้งสำหรับผู้ใช้ทั่วไป
