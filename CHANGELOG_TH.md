# LumaCue บันทึกการเปลี่ยนแปลง

บันทึกการเปลี่ยนแปลงภาษาไทยสำหรับ LumaCue รุ่นปัจจุบันและรุ่นใหม่ต่อจากนี้ ดูประวัติทั้งหมดภาษาอังกฤษได้ที่ [CHANGELOG.md](CHANGELOG.md)

## 0.8.0 - ความเสถียรของ Twitch และการเริ่มต้นรองรับภาษา

### เพิ่ม
- เพิ่มปุ่ม Reconnect สำหรับ Broadcaster เพื่อยืนยัน Twitch ใหม่โดยไม่ล้าง reward, EventSub หรือ fixed bot
- เพิ่มสิทธิ์ `user:read:chat` สำหรับ Broadcaster เพื่อให้ LumaCue รับคำตอบเลือกศิลปินจากผู้ชมได้เมื่อใช้ `xyhoxx_bot` แบบ server-side
- เพิ่มสวิตช์เปิด/ปิด Channel Points redemption โดยคง reward ที่เลือกและการตั้งค่า listener ไว้

### เปลี่ยนแปลง
- ทำให้คำขอจาก Twitch ใช้การ sanitize แบบเดียวกับ desktop: normalize Unicode, ลบอักขระซ่อน, ตัด trigger ที่รองรับ และรวมช่องว่าง
- ภาษาอังกฤษเป็นภาษาที่ใช้ได้ใน release ปัจจุบัน ส่วนตัวเลือกภาษาไทยยังแสดงเพื่อเตรียม UI responsive ในรอบถัดไป

### แก้ไข
- แก้ flow เลือกเพลง `1/2/3` จาก Twitch ที่เคยส่งคำถามได้แต่รับคำตอบไม่ได้ในโหมด fixed server-side bot
- แก้การตีความคำค้นจาก redemption ที่ไม่ตรงกับการค้นหาจาก desktop
- ลบหัวข้อ `Request Song reward` ที่ซ้ำซ้อนออกจาก Channel Points card
- นำ Album Motion ออกจาก Player และ OBS overlay เพราะยังไม่เหมาะกับทิศทางผลิตภัณฑ์

## 0.7.9 - นำเข้า Spotify Playlist

- เพิ่มการนำเข้า Spotify playlist ผ่านแท็บ Playlist เดิม
- อ่านข้อมูลสาธารณะจาก Spotify embed แล้วแปลงเป็นคำค้น title/artist เพื่อค้นหาเพลงที่เล่นได้ด้วย YouTube Music หรือ YouTube
- ช่อง Playlist รองรับทั้งลิงก์ YouTube และ Spotify

## 0.7.0 ถึง 0.7.8 - สรุปภาษาไทย

- เพิ่ม Global Blocklist, Local Music, Auto DJ discovery และ fixed server-side `xyhoxx_bot`
- ปรับ desktop player shell, Library tabs, liquid toggles, OBS overlay และ Discord Rich Presence ให้เสถียรและใช้งานง่ายขึ้น
- เพิ่ม CI/CD release flow, app/runtime split update packages และ cleanup สำหรับ cache ของตัวอัปเดต

สำหรับรายละเอียดเชิงเทคนิคและประวัติ release ก่อนหน้า โปรดดู [CHANGELOG.md](CHANGELOG.md)
