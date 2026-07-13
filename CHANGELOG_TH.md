# LumaCue บันทึกการเปลี่ยนแปลง

บันทึกการเปลี่ยนแปลงภาษาไทยของ LumaCue ครอบคลุมทุกรุ่นที่เผยแพร่สู่สาธารณะ ตั้งแต่ `0.1.1` ถึงรุ่นปัจจุบัน ดูรายละเอียดเชิงเทคนิคภาษาอังกฤษได้ที่ [CHANGELOG.md](CHANGELOG.md)

**ภาษา:** [English](CHANGELOG.md) | [ภาษาไทย](CHANGELOG_TH.md)

## 0.8.0 - ความเสถียรของ Twitch และการเริ่มต้นรองรับภาษา

### เพิ่ม
- เพิ่มปุ่ม Reconnect สำหรับ Broadcaster เพื่อเชื่อมต่อ Twitch ใหม่โดยไม่ล้าง reward, EventSub หรือบอทที่ระบบจัดการให้
- เพิ่มสิทธิ์ `user:read:chat` สำหรับ Broadcaster เพื่อให้ LumaCue รับคำตอบเลือกศิลปินจากผู้ชมได้เมื่อใช้ `xyhoxx_bot` ที่ระบบจัดการให้
- เพิ่มสวิตช์เปิด/ปิดการแลก Channel Points โดยคง reward ที่เลือกและการตั้งค่ารับคำขอเพลงไว้

### เปลี่ยนแปลง
- ทำให้คำขอจาก Twitch ถูกจัดรูปแบบเหมือนการค้นหาจากโปรแกรม: ปรับ Unicode, ลบอักขระซ่อน, ตัดคำสั่งนำหน้า และรวมช่องว่าง
- release ปัจจุบันใช้ภาษาอังกฤษ ส่วนตัวเลือกภาษาไทยยังแสดงเพื่อเตรียมปรับหน้าตาให้รองรับข้อความภาษาไทยในรอบถัดไป

### แก้ไข
- แก้การเลือกเพลง `1/2/3` จาก Twitch ที่เคยส่งคำถามได้แต่รับคำตอบไม่ได้เมื่อใช้บอทที่ระบบจัดการให้
- แก้คำค้นจากการแลกแต้มที่ตีความไม่ตรงกับการค้นหาจากโปรแกรม
- ลบหัวข้อ `Request Song reward` ที่ซ้ำซ้อนออกจาก Channel Points card
- นำ Album Motion ออกจาก Player และ OBS overlay เพราะยังไม่เหมาะกับทิศทางของโปรแกรม

## 0.7.9 - นำเข้าเพลย์ลิสต์ Spotify

- เพิ่มการนำเข้า Spotify playlist ผ่านแท็บ Playlist เดิม
- อ่านข้อมูลสาธารณะจาก Spotify embed แล้วแปลงเป็นคำค้น title/artist เพื่อค้นหาเพลงที่เล่นได้ด้วย YouTube Music หรือ YouTube
- ช่อง Playlist รองรับทั้งลิงก์ YouTube และ Spotify

## 0.7.8 - ปรับ Album Motion สำหรับ Overlay

- ทำให้ Album Motion ใช้กับ overlay แบบ compact และ pill ได้ดีขึ้น พร้อมลดปัญหาภาพเคลื่อนไหวเป็นสี่เหลี่ยมด้านหลังการ์ด

## 0.7.7 - ปรับ interaction และความเสถียร

- เพิ่มเส้นใต้แท็บ Library ที่เคลื่อนไหวต่อเนื่อง, ทำสวิตช์ให้ใช้รูปแบบเดียวกัน และแก้ Discord RPC เมื่อเปลี่ยนเพลงเร็ว

## 0.7.6 - แก้รอยต่อของหน้า Player

- ทำให้ backdrop ของ artwork เปลี่ยนหน้าได้เนียนขึ้น และแก้พื้นที่ว่างด้านขวาของแท็บ Library

## 0.7.5 - CI/CD และแก้ Auto DJ

- ใช้ CI/CD เป็นช่องทางปล่อยเวอร์ชันหลัก, แก้ Auto DJ ให้เริ่มหาเพลงได้แม้คิวว่าง และปรับไอคอน installer

## 0.7.4 - แก้ไอคอน Windows

- ให้ไอคอนบน Desktop และ Start Menu เปลี่ยนตามอัปเดตได้โดยไม่ต้องติดตั้งใหม่

## 0.7.3 - ปรับแบรนด์และข้อมูลระหว่างพัฒนา

- ใช้โลโก้ LumaCue แบบวงกลมในหน้าหลัก, launcher และ tray พร้อมแยกข้อมูล Local Music ของเครื่องพัฒนาออกจาก source code

## 0.7.2 - เก็บกวาดไฟล์อัปเดตค้าง

- ทำให้การลบไฟล์เวอร์ชันเก่าและไฟล์ดาวน์โหลดของ updater ทนต่อกรณี Windows ล็อกไฟล์ชั่วคราว

## 0.7.1 - ลดเพลงซ้ำใน Auto DJ

- Auto DJ จะหลีกเลี่ยงเพลงที่เพิ่งเล่นไป และ launcher เก็บกวาดไฟล์เวอร์ชันเก่าได้เชื่อถือขึ้น

## 0.7.0 - ความปลอดภัยของคำขอเพลงและ Auto DJ

- เพิ่ม Global Blocklist, ปรับ Auto DJ และ Local Music, เพิ่มบอท `xyhoxx_bot` ที่ระบบจัดการให้ และเกลาหน้า desktop

## 0.6.8 - เกลาหน้ายืนยัน Twitch

- หลังเชื่อม Twitch สำเร็จ URL ในเบราว์เซอร์จะไม่เก็บ OAuth ticket ไว้

## 0.6.7 - แก้ Twitch OAuth error 1010

- แก้ callback ของ Cloudflare Worker ที่ถูก Twitch ปฏิเสธในบางกรณี

## 0.6.6 - Twitch OAuth Broker

- เพิ่ม Cloudflare Worker สำหรับเชื่อม Twitch แบบปลอดภัย โดยไม่ฝัง client secret ไว้ในโปรแกรม

## 0.6.5 - Auto DJ และ Twitch session

- เพิ่มการบีบอัดไฟล์ Local Music เมื่อทำได้ และแก้สถานะ Twitch session หมดอายุให้แสดงถูกต้อง

## 0.6.4 - ล้าง Discord Presence ค้าง

- ล้างสถานะ LumaCue ใน Discord เมื่อเปิดโปรแกรมโดยไม่มีเพลง หรือเมื่อปิดโปรแกรม

## 0.6.3 - เก็บกวาดแคชการติดตั้ง

- ลบ ZIP และไฟล์ staging ที่ updater ไม่ใช้แล้ว โดยเก็บข้อมูลผู้ใช้และ runtime ที่กำลังใช้งานไว้

## 0.6.2 - Discord IPC ในตัว

- เพิ่มการเชื่อม Discord RPC ผ่าน IPC โดยตรง ลดการพึ่งพาไลบรารีภายนอกที่ทำให้โปรแกรมพัง

## 0.6.1 - แก้ Discord RPC crash

- แก้ error ที่ทำให้ main process พังเมื่อ Discord IPC ถูกตัดระหว่างอัปเดตสถานะ

## 0.6.0 - Local Music และ Auto DJ

- เพิ่มการนำเข้าเพลงในเครื่อง, เล่นผ่าน Player เดิม และให้ Auto DJ หาเพลงต่อจากข้อมูลการฟัง

## 0.5.0 - ออกแบบ Player ใหม่

- ยกเครื่องหน้าตา Player, artwork backdrop, queue panel, overlay และสถานะ Discord ให้เป็นประสบการณ์เพลงที่ชัดเจนขึ้น

## 0.4.0 - วางรากฐาน Desktop UI

- วาง design system และโครงหน้าจอ desktop ใหม่ รวมถึง shell, navigation, Twitch setup และ themed dialog

## 0.3.5 - แก้ backend เปิดไม่ขึ้น

- เพิ่ม `history.py` เข้าแพ็กเกจเพื่อแก้ backend หยุดทำงานใน release ที่ได้รับผลกระทบ

## 0.3.4 - เก็บกวาด Resolver

- ลบพารามิเตอร์และเอกสารเก่าที่ไม่ใช้งานออกจากตัวค้นหาเพลง

## 0.3.3 - ตรวจ Resolver และ redemption

- รวมกติกาการให้คะแนนเพลง, เก็บ dead code และทำให้การคืนแต้ม Channel Points ครอบคลุมกรณีเลือกศิลปิน

## 0.3.2 - Play Analytics

- เพิ่มข้อมูลวิเคราะห์การเล่นเพลง และแก้การรวมโมดูล backend ในแพ็กเกจ

## 0.3.1 - คืน Channel Points อัตโนมัติ

- คืนแต้มเมื่อเพลงถูกข้าม ลบ หรือเล่นไม่ได้ แทนการถือว่า redemption สำเร็จตั้งแต่เข้าคิว

## 0.3.0 - รองรับลิงก์ Spotify

- เพิ่มการรับลิงก์ Spotify track และแปลงเป็นคำค้นเพลงที่เล่นได้

## 0.2.28 - เก็บ learned rules ให้ต่อเนื่อง

- ทำให้กติกาที่เรียนรู้จากการเลือกเพลงอ้างอิงคำขอเดิมได้ถูกต้อง และลด toast Twitch ซ้ำ

## 0.2.27 - แสดงสถานะ Device Login ถูกต้อง

- ซ่อน panel device code เมื่อเชื่อม Twitch สำเร็จ

## 0.2.26 - เข้ารหัส Twitch token

- เก็บ access และ refresh token ด้วย Windows DPAPI และย้ายข้อมูลเดิมให้อัตโนมัติ

## 0.2.25 - สถานะ Twitch และการจำการตั้งค่า

- ปรับสถานะบัญชีตามวันหมดอายุ token และเก็บ reward กับข้อความทดสอบไว้ในโปรแกรม

## 0.2.24 - จัด layout Player แยกหน้าต่าง

- แก้ artwork และปุ่มควบคุมไม่ให้ทับกันนอก desktop shell

## 0.2.23 - แยกเพลงชื่อไทยซ้ำกัน

- เพิ่มการตรวจเพลงชื่อไทยที่มีหลายศิลปิน และให้ผู้ชมเลือกผลลัพธ์ได้

## 0.2.22 - ต่ออายุ Twitch token อัตโนมัติ

- รีเฟรช token ระหว่างใช้งานและลองคำขอใหม่เมื่อ Twitch ตอบ 401

## 0.2.21 - จับคู่ชื่อเพลงไทยที่ต่างรูปแบบ

- ให้ learned rules รองรับชื่อไทยแบบย่อหรือแบบเต็มมากขึ้น

## 0.2.20 - เล่นเพลงที่ embed ไม่ได้

- ใช้ direct audio เมื่อวิดีโอ YouTube เล่นผ่าน embed ไม่ได้ หากเพลงยังเข้าถึงได้

## 0.2.19 - สตรีม direct audio

- เพิ่มเส้นทางเล่นเสียงโดยตรงสำหรับวิดีโอที่มีข้อจำกัดกับ embed

## 0.2.18 - คัดกรองผล fallback

- ลดการเลือก live, concert และเวอร์ชันที่ไม่ตรงกับคำขอระหว่าง fallback

## 0.2.17 - ตรวจ embed ก่อนเข้าคิว

- ตรวจความสามารถในการเล่นผ่าน embed ก่อนรับเพลง และให้ feedback ที่ชัดเจนขึ้น

## 0.2.16 - fallback เมื่อ embed error

- เพิ่มทางเลือกค้นหาและเล่นเพลงเมื่อ YouTube embed รายการแรกผิดพลาด

## 0.2.15 - เลือกผลลัพธ์แบบตัวเลข

- เพิ่มการตอบ `1/2/3` เพื่อเลือกศิลปินหรือเพลงที่ชื่อซ้ำ

## 0.2.14 - เลือก Channel Points reward

- ให้เลือก reward ที่มีอยู่ หรือสร้าง/อัปเดต reward จาก LumaCue

## 0.2.13 - สอน resolver ด้วย URL

- แก้การบันทึกกติกาเลือกเพลงผ่าน YouTube URL

## 0.2.12 - ปรับ guard ของ resolver

- ป้องกันผลค้นหาที่ไม่ตรงคำขอและแก้เงื่อนไขคัดกรองหลายจุด

## 0.2.11 - แสดงจำนวน Quick Add

- แสดงจำนวนผลลัพธ์และจัดการสถานะ Quick Add ให้ชัดเจนขึ้น

## 0.2.10 - จัดอันดับคำแนะนำ

- ปรับคะแนนและลำดับเพลงใน suggestion list

## 0.2.9 - ตรวจ artist hint

- ใช้ชื่อศิลปินในคำขอเพื่อกันการเลือกเพลงชื่อซ้ำผิดรายการ

## 0.2.8 - fallback ค้นหาวิดีโอ

- ค้นหาจาก YouTube videos เพิ่มเมื่อคลังเพลงของ YouTube Music ไม่มีผลลัพธ์

## 0.2.7 - launcher และ EventSub

- เพิ่มการอัปเดต launcher และทำให้ EventSub เสถียรขึ้น

## 0.2.6 - EventSub reconnect

- ลดการ reconnect วนและจัดการ token หมดอายุก่อนเชื่อม EventSub ใหม่

## 0.2.5 - fallback สำหรับคำค้นไทย

- แยกคำไทยเพื่อค้นหาใหม่เมื่อผลลัพธ์แบบติดกันไม่พบเพลง

## 0.2.4 - สอนเพลงจาก YouTube URL

- ให้ผู้ใช้กำหนดผลลัพธ์ที่ต้องการผ่านลิงก์ YouTube

## 0.2.3 - ปรับ Queue Drawer และ resolver

- เกลาการลากเรียงคิวและปรับเกณฑ์เลือกเพลง

## 0.2.2 - การเปิดโปรแกรมและ IPC

- ลดเวลาเปิด desktop app และปรับการสื่อสารระหว่าง shell กับ backend

## 0.2.1 - animation ของ desktop และ player

- เพิ่ม motion สำหรับ toast, dialog, navigation, queue, player และ OBS overlay

## 0.2.0 - Resolver Learning

- เพิ่มการจดจำการเลือกเพลง เช่น เลือกเสมอ, ไม่เลือก และเลือกเพลงนี้

## 0.1.42 - ตรวจสอบไฟล์อัปเดตและ build pipeline

- เพิ่มการตรวจ hash ของ launcher และจัดระเบียบคำสั่ง build/release

## 0.1.41 - ถอนการติดตั้งและอัปเดต launcher

- แก้การถอนการติดตั้ง เพิ่ม self-update ของ launcher และเพิ่มการลองใหม่เมื่อแตกไฟล์ไม่สำเร็จ

## 0.1.40 - ตั้งชื่อ installer

- ปรับชื่อไฟล์ installer และแยก offline/online setup ให้เข้าใจง่าย

## 0.1.39 - Native Setup Experience

- เปลี่ยนไปใช้ setup stub แบบ native เพื่อให้ขั้นตอนติดตั้งชัดเจนขึ้น

## 0.1.38 - ASAR Extraction

- แก้ปัญหาการแตกไฟล์ `.asar` ระหว่างติดตั้งและอัปเดต

## 0.1.37 - Web Installer

- เพิ่ม web installer ที่ลง launcher ก่อน แล้วให้ launcher ดาวน์โหลดโปรแกรม

## 0.1.36 - Silent Installer Launch

- ให้ launcher แสดงความคืบหน้าแทนหน้าต่าง installer ระหว่างติดตั้งเบื้องหลัง

## 0.1.35 - Hidden Installer Attempt

- ทดลองลดหน้าต่าง installer ที่รบกวนผู้ใช้ระหว่างอัปเดต

## 0.1.34 - Installer Window Suppression

- ปรับการซ่อนหน้าต่าง installer และแก้การเปิดโปรแกรมหลังติดตั้ง

## 0.1.33 - Launcher-First Install UI

- ให้ launcher เป็นหน้าหลักของขั้นตอนติดตั้งและอัปเดต

## 0.1.32 - Patch Staging Copy

- ปรับการ copy ไฟล์สำหรับ patch update ให้เร็วขึ้นและไม่คัดลอก runtime ซ้ำ

## 0.1.31 - Silent Installer with Launcher UI

- รวมการติดตั้งเงียบกับ UI แสดงสถานะของ launcher

## 0.1.30 - Faster Restart to Apply

- ลดเวลารอก่อนเปิดโปรแกรมใหม่หลังใช้การอัปเดต

## 0.1.29 - Custom Update Dialog

- เพิ่มหน้าต่างแจ้งการอัปเดตของ LumaCue แทน dialog ของระบบ

## 0.1.28 - Single Instance and Launcher Cleanup

- ป้องกันการเปิดหลายหน้าต่างพร้อมกันและเก็บกวาด launcher state

## 0.1.27 - Patch Update and Launcher UI Fixes

- เพิ่ม patch update และแก้ UI/การส่งต่อการเปิดโปรแกรมของ launcher

## 0.1.26 - Download Cache Cleanup

- ลบไฟล์ดาวน์โหลดและ manifest เก่าหลังอัปเดตโดยไม่ลบข้อมูลผู้ใช้

## 0.1.25 - Fresh Install Detection

- ป้องกัน launcher ดาวน์โหลดซ้ำทันทีหลังติดตั้งเวอร์ชันเดียวกัน

## 0.1.24 - Streaming Extraction

- แตกไฟล์อัปเดตแบบต่อเนื่องเพื่อลดการใช้หน่วยความจำ

## 0.1.23 - Faster Extraction and Cache

- เร่งการแตกไฟล์และใช้ cache ที่ดาวน์โหลดแล้วเมื่อปลอดภัย

## 0.1.22 - JavaScript Extraction Only

- ย้ายการแตกไฟล์อัปเดตออกจาก PowerShell มาใช้ JavaScript ในโปรแกรม

## 0.1.21 - แก้ launcher ค้าง

- แก้ launcher ค้างหลังขั้นตอน apply update และเพิ่มการตรวจสถานะที่จำเป็น

## 0.1.20 - สถานะ EventSub และ patch stability

- ทำให้สถานะ EventSub อัปเดตหลังเริ่ม listener และปรับความเสถียรของ patch

## 0.1.19 - EventSub สองการเชื่อมต่อ

- แยก EventSub ของ Broadcaster และ Bot เป็น WebSocket คนละเส้นตามสิทธิ์ Twitch

## 0.1.18 - Native Extraction Path

- ใช้เส้นทางแตกไฟล์แบบ native และแก้ compatibility ของ update package

## 0.1.17 - ความคืบหน้าการแตกไฟล์

- แสดงความคืบหน้าขณะเตรียมไฟล์อัปเดตให้ชัดเจนขึ้น

## 0.1.16 - เก็บกวาด EventSub subscription

- ลบ subscription เก่าก่อนสร้างใหม่เพื่อป้องกัน listener ซ้ำ

## 0.1.15 - ป้องกัน Twitch login คนละแอป

- ตรวจ Client ID ของ token ที่บันทึกไว้และให้เชื่อมใหม่เมื่อไม่ตรงกับแอป LumaCue

## 0.1.14 - Runtime Split Manifest

- เพิ่ม manifest ที่แยก app package ออกจาก runtime package สำหรับอัปเดตที่เล็กลง

## 0.1.13 - รองรับ launcher รุ่นเก่า

- ให้ manifest ใหม่ยังทำงานกับ launcher รุ่นก่อนหน้าได้

## 0.1.12 - Unified Startup Handoff

- รวมขั้นตอนส่งต่อจาก launcher ไป desktop app ให้เป็นเส้นทางเดียว

## 0.1.11 - เปลี่ยนไปใช้ Patch Updater

- เริ่มใช้ patch update และรองรับ shared runtime ระหว่างเวอร์ชัน

## 0.1.10 - เกลาหน้า About และ Updates

- ลบการ์ด runtime ที่ซ้ำซ้อน และเขียน release notes แบบ UTF-8 ไม่มี BOM

## 0.1.9 - Native Zip Update Apply

- เปลี่ยนการแตก ZIP update เป็น native Node process และเพิ่มการตรวจ staged app

## 0.1.8 - Launcher Handoff Cleanup

- แก้การส่งต่อจาก launcher หลังอัปเดตและเก็บไฟล์ชั่วคราวให้เรียบร้อย

## 0.1.7 - รากฐาน Custom Launcher

- วาง launcher ของ LumaCue สำหรับตรวจและติดตั้ง update ก่อนเปิด desktop app

## 0.1.6 - About และสถานะอัปเดต

- เพิ่มหน้า About / Updates พร้อมเวอร์ชัน, สถานะ update, ความคืบหน้า และ OBS URL

## 0.1.5 - Shortcut Metadata

- ปรับ metadata ของ shortcut และการเปิดแอปจาก Windows

## 0.1.4 - Startup Update Screen

- เพิ่มหน้าจอตรวจและติดตั้ง update ตอนเปิดโปรแกรม

## 0.1.3 - Silent Update Install

- ติดตั้ง update เบื้องหลังโดยให้ LumaCue แสดงสถานะแทน

## 0.1.2 - เกลารุ่นแพ็กเกจ desktop

- ปรับการแพ็กโปรแกรมและประสบการณ์ใช้งานหลังติดตั้ง

## 0.1.1 - Public Auto-Update Baseline

- ปล่อย LumaCue desktop รุ่นสาธารณะแรก พร้อม installer และระบบอัปเดตอัตโนมัติ
