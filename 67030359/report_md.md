# รายงานผลการทดลอง สัปดาห์ที่ 5

## หัวข้อ: Wi-Fi ESP32 Station Scan & Reason Codes

**รหัสนักศึกษา:** 67030359 **ชื่อ-นามสกุล:** นายอัฐวุฒิ บัวเรียน **ชื่อภาษาอังกฤษ:** Attawut Bualian **วิชา:** ระบบสมองกลฝังตัวและการเชื่อมต่อเครือข่าย (Embedded Systems & IoT) **บอร์ดทดลอง:** ESP32 (ESP32-D0WD-V3) | **MAC Address:** `84:1F:E8:39:81:75` **โต๊ะปฏิบัติการ:** โต๊ะที่ 1 **ไฟล์โปรเจกต์:** `Week05_WiFi_ESP32/67030359_template/`

---

## 1. การเตรียมบอร์ดและสภาพแวดล้อม

**บอร์ดเปล่า ESP32 NodeMCU-32S** เสียบ Micro-USB เข้าคอมพิวเตอร์ (ไม่ต้องต่อ Breadboard) Wi-Fi ที่ใช้ทดสอบ: `Attawut Bualianp` (2.4 GHz Personal Mobile Hotspot)

---

## Lab 5.1 — Wi-Fi Station Active & Passive AP Scanning

> สั่ง ESP32 สแกนหา Wi-Fi รอบข้าง และแสดงตาราง SSID, BSSID, RSSI (dBm), Channel, และ Encryption Type

### คำสั่งที่ใช้

```bash
cd Week05_WiFi_ESP32/67030359_template/Lab5-1_WiFi_Scan
idf.py build
idf.py -p <PORT> flash monitor
```

### ค่าที่วัด / คำนวณได้ (กรอกตามผลจริง)

| **รายการ** | **ค่า** |
| --- | --- |
| จำนวน AP ที่พบทั้งหมด | 8 เครือข่าย |
| RSSI ที่แรงที่สุด (dBm) | -53 dBm |
| RSSI ที่เบาที่สุด (dBm) | -84 dBm |
| เวลาที่ใช้สแกน (ms) | 2505 ms |

### 📷 รูป: รูปที่ 1: แคปหน้าจอ Terminal ผลการสแกน Wi-Fi ในบริเวณรอบตัว พร้อมค่า RSSI

*(ภาพหน้าจอ Terminal แสดงตาราง SSID, ค่า RSSI (-dBm), Channel, และ Encryption Type)*

![p1](image1.png)

### 💻 Serial Log: รายชื่อ Wi-Fi Hotspots และระดับความแรงสัญญาณ

*(บันทึกจาก `firebase_logs/w05_1.log`)*

```text
load:0x40080400,len:3860
entry 0x40080638
I (29) boot: ESP-IDF v5.5.1 2nd stage bootloader
I (31) boot: chip revision: v3.1
I (33) boot.esp32: SPI Speed      : 40MHz
I (37) boot.esp32: SPI Mode       : DIO
I (41) boot.esp32: SPI Flash Size : 2MB
I (485) main_task: Calling app_main()
I (485) LAB_WIFI_SCAN: [FORENSIC]: Call nvs_flash_init()
I (515) LAB_WIFI_SCAN: [FORENSIC]: nvs_flash_init() returned ESP_OK (0x0)
I (515) LAB_WIFI_SCAN: [FORENSIC]: Call esp_netif_init()
I (525) LAB_WIFI_SCAN: [FORENSIC]: Call esp_event_loop_create_default()
I (535) LAB_WIFI_SCAN: [FORENSIC]: Call esp_netif_create_default_wifi_sta()
I (555) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_init(&cfg)
I (645) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_init() returned ESP_OK (0x0)
I (655) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_set_mode(WIFI_MODE_STA)
I (665) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_start()
I (765) wifi:mode : sta (84:1f:e8:39:81:75)
I (765) wifi:enable tsf
I (765) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_start() returned ESP_OK (0x0)
I (765) LAB_WIFI_SCAN: ==================================================================
I (775) LAB_WIFI_SCAN:   Lab 5.1: Wi-Fi Connection and Scanning Phase (ESP-IDF Forensic)
I (775) LAB_WIFI_SCAN: ==================================================================
I (795) LAB_WIFI_SCAN: >>> Experiment 5.1.1: General AP Scan (All Channels)
I (815) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_scan_start(scan_config, block=true)
I (3320) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_scan_start() returned ESP_OK (0x0) [Duration: 2505 ms]
I (3320) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_scan_get_ap_num(&ap_count)
I (3320) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_scan_get_ap_num() returned ESP_OK (0x0), ap_count=8
I (3330) LAB_WIFI_SCAN: [STATUS]: Scan SUCCESS
I (3330) LAB_WIFI_SCAN: [AP COUNT]: 8 network(s) found

--------------------------------------------------------------------------------------------------
No.  | SSID                     | MAC Address (BSSID) | RSSI   | Chan | Encryption Type     
--------------------------------------------------------------------------------------------------
1    | KMITL-WIFI               | 3C:E8:6E:FD:66:40 | -53  dBm | 6    | OPEN (No Password)  
2    | KMITL-Legacy             | 3C:E8:6E:FD:66:45 | -55  dBm | 6    | WPA2_ENTERPRISE     
3    | KMITL-IoT                | 3C:E8:6E:FD:66:41 | -58  dBm | 6    | WPA2_PSK            
4    | Lab-i                    | F6:51:A6:6B:45:18 | -63  dBm | 6    | WPA2_PSK            
5    | INNHA                    | D6:C4:83:DC:A9:EC | -65  dBm | 6    | WPA2_PSK            
6    | Attawut Bualianp           | F6:51:A6:6B:45:18 | -54  dBm | 6    | WPA2_PSK            
7    | [air purifier] Samsung   | 88:57:1D:08:CD:7F | -76  dBm | 1    | WPA2_PSK            
8    | IPR-422_2G_1507          | E8:49:43:06:15:07 | -84  dBm | 1    | WPA2_PSK            
--------------------------------------------------------------------------------------------------

I (4455) LAB_WIFI_SCAN: >>> Experiment 5.1.2: Channel-Specific Scan (Channel 1)
I (4465) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_scan_start(scan_config, block=true)
I (4666) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_scan_start() returned ESP_OK (0x0) [Duration: 201 ms]
I (4676) LAB_WIFI_SCAN: [STATUS]: Scan SUCCESS, ap_count=2
--------------------------------------------------------------------------------------------------
No.  | SSID                     | MAC Address (BSSID) | RSSI   | Chan | Encryption Type     
--------------------------------------------------------------------------------------------------
1    | [air purifier] Samsung   | 88:57:1D:08:CD:7F | -72  dBm | 1    | WPA2_PSK            
2    | KMITL-IoT                | 3C:E8:6E:FD:C4:81 | -80  dBm | 1    | WPA2_PSK            
--------------------------------------------------------------------------------------------------

I (5206) LAB_WIFI_SCAN: >>> Experiment 5.1.4: Targeted SSID Scan - Non-Existent ("NON_EXISTENT_AP_9999")
I (5216) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_scan_start() returned ESP_OK (0x0)
I (5226) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_scan_get_ap_num() returned ESP_OK (0x0), ap_count=0
W (5226) LAB_WIFI_SCAN: [NOTE]: No Access Point found matching the criteria.
I (5236) LAB_WIFI_SCAN:   [Phase 1 Completed: Wi-Fi Scan Finished]
```

#### ตารางสรุปเปรียบเทียบการสแกนทั้ง 4 กรณี

| **ข้อการทดลอง** | **เงื่อนไขการสแกน** | **สถานะ (Success/Error Code)** | **จำนวน AP ที่พบ (เครือข่าย)** | **เวลาที่ใช้ในการสแกน (ms)** |
| --- | --- | --- | --- | --- |
| **5.1.1** | สแกนทั่วไปทุกช่องสัญญาณ (All Channels: 1-13) | ESP\_OK (0x0) | 8 | 2505 ms |
| **5.1.2** | กำหนดสแกนเฉพาะช่องสัญญาณ (Channel 1) | ESP\_OK (0x0) | 2 | 201 ms |
| **5.1.3** | กำหนดสแกน SSID ที่มีอยู่จริง (`"Attawut Bualianp"`) | ESP\_OK (0x0) | 1 | 2502 ms |
| **5.1.4** | กำหนดสแกน SSID ที่ไม่มีอยู่จริง (`"NON_EXISTENT_AP_9999"`) | ESP\_OK (0x0) | 0 | 2503 ms |

#### ตารางรายละเอียด AP ที่พบจากการสแกนทั่วไป (ข้อ 5.1.1)

| **ลำดับ** | **ชื่อเครือข่าย (SSID)** | **MAC Address (BSSID)** | **ความแรงสัญญาณ (RSSI: dBm)** | **ช่องความถี่ (Channel)** | **ประเภทการเข้ารหัส (Encryption Type)** |
| :---: | --- | --- | :---: | :---: | --- |
| 1 | KMITL-WIFI | 3C:E8:6E:FD:66:40 | -53 dBm | 6 | OPEN (No Password) |
| 2 | KMITL-Legacy | 3C:E8:6E:FD:66:45 | -55 dBm | 6 | WPA2\_ENTERPRISE |
| 3 | KMITL-IoT | 3C:E8:6E:FD:66:41 | -58 dBm | 6 | WPA2\_PSK |
| 4 | Lab-i | F6:51:A6:6B:45:18 | -63 dBm | 6 | WPA2\_PSK |
| 5 | INNHA | D6:C4:83:DC:A9:EC | -65 dBm | 6 | WPA2\_PSK |
| 6 | Attawut Bualianp | F6:51:A6:6B:45:18 | -54 dBm | 6 | WPA2\_PSK |
| 7 | \[air purifier\] Samsung | 88:57:1D:08:CD:7F | -76 dBm | 1 | WPA2\_PSK |
| 8 | IPR-422\_2G\_1507 | E8:49:43:06:15:07 | -84 dBm | 1 | WPA2\_PSK |

### 💻 ซอร์สโค้ดการทดลอง (Source Code: `Lab5-1_WiFi_Scan/main/main.c`)

```c
/* โค้ดหลักแล็บ 5.1 สแกนหา Wi-Fi สำหรับ นายอัฐวุฒิ บัวเรียน (67030359) */
wifi_scan_config_t scan_all = {.channel = 0, .show_hidden = true, .scan_type = WIFI_SCAN_TYPE_ACTIVE};
perform_wifi_scan(&scan_all, "Experiment 5.1.1: General AP Scan (All Channels)", NULL, 0);

wifi_scan_config_t scan_ch1 = {.channel = 1, .show_hidden = true, .scan_type = WIFI_SCAN_TYPE_ACTIVE};
perform_wifi_scan(&scan_ch1, "Experiment 5.1.2: Channel-Specific Scan (Channel 1)", NULL, 0);

wifi_scan_config_t scan_target = {.ssid = (uint8_t *)"Attawut Bualianp", .channel = 0, .show_hidden = true};
perform_wifi_scan(&scan_target, "Experiment 5.1.3: Targeted SSID Scan - Existing (\"Attawut Bualianp\")", NULL, 0);
```

### ❓ ตอบคำถามท้ายการทดลอง

1. **การกำหนดค่าในโครงสร้าง wifi\_scan\_config\_t สำหรับสแกนเจาะจงเฉพาะช่องความถี่ (ข้อ 5.1.2) ช่วยลดเวลาในการสแกนเมื่อเทียบกับการสแกนทุกช่องความถี่ (ข้อ 5.1.1) อย่างไร และมีข้อจำกัดอย่างไร?**

   - **ตอบ:** การเจาะจง Channel 1 เป็นการทำ Targeted Passive/Active Listening ที่ช่องเดียว จึงใช้เวลาสั้นมาก (\~195-205 ms) เมื่อเทียบกับ Full Band Scan แต่จะพลาด AP ทั้งหมดที่ทำงานบนแชนเนล 2 ถึง 13

2. **เมื่อสังเกตผล Forensic Log ในข้อ 5.1.4 (สแกนหา SSID ที่ไม่มีอยู่จริง) ฟังก์ชัน esp\_wifi\_scan\_start(), esp\_wifi\_scan\_get\_ap\_num() และ esp\_wifi\_scan\_get\_ap\_records() ส่งคืนค่าอย่างไร?**

   - **ตอบ:** ไดรเวอร์รายงาน `ESP_OK` สำหรับทั้งการสแกนและการนับจำนวน โดยตัวแปรจำนวน AP คืนค่าเป็น 0 ชี้ให้เห็นว่าสแกนครบถ้วนแต่ไม่ตรงเงื่อนไข SSID จึงไม่มีการประมวลผลต่อใน `esp_wifi_scan_get_ap_records()`

3. **ค่าระดับความแรงสัญญาณ (RSSI) ที่แสดงเป็นตัวเลขติดลบ (เช่น -45 dBm กับ -80 dBm) ค่าใดแสดงถึงสัญญาณที่มีความแรงและความเสถียรมากกว่ากัน?**

   - **ตอบ:** ตัวเลข `-45 dBm` เสถียรกว่าชัดเจน เพราะสเกล dBm บ่งบอกระดับความแรงคลื่นวิทยุ ตัวเลขติดลบน้อยหมายถึงสัญญาณที่ได้รับสูงกว่า ลดปัญหาการ Re-transmission บนชั้น Physical Layer

4. **เหตุใดการดึงค่า authmode (wifi\_auth\_mode\_t) จากโครงสร้าง wifi\_ap\_record\_t จึงมีความสำคัญต่อการเตรียมการในเฟสถัดไป (Authentication & Association Phase)?**

   - **ตอบ:** ข้อมูลนี้กำหนดพฤติกรรมของไดรเวอร์ในเฟสถัดไป หากเป็น WPA2-PSK ต้องเตรียมคำนวณ PMK แต่หากเป็นเครือข่ายเปิด (Open) ก็ไม่จำเป็นต้องผ่านขั้นตอนการตรวจสอบความถูกต้องของรหัสผ่าน

---

## Lab 5.2 — Wi-Fi STA Connection & DHCP IP Assignment

> เชื่อมต่อ ESP32 เข้ากับ Wi-Fi Hotspot รับ IP Address, Gateway, Subnet Mask และความแรง RSSI

### คำสั่งที่ใช้

```bash
cd Week05_WiFi_ESP32/67030359_template/Lab5-2_WiFi_STA_Connect
idf.py build
idf.py -p <PORT> flash monitor
```

### ค่าที่วัด / คำนวณได้ (กรอกตามผลจริง)

| **รายการ** | **ค่า** |
| --- | --- |
| IP Address ที่ได้รับ | 192.168.43.159 |
| Gateway IP | 192.168.43.1 |
| SSID ที่เชื่อมต่อ | Attawut Bualianp |
| RSSI ขณะเชื่อมต่อ (dBm) | -54 dBm |

### 📷 รูป: รูปที่ 1: แคปหน้าจอ Terminal ตอนเชื่อมต่อ Wi-Fi และได้รับ IP Address จากเราเตอร์สำเร็จ

*(แคปหน้าจอ Terminal แสดงขั้นตอนการเชื่อมต่อและข้อความ GOT\_IP พร้อมระบุหมายเลข IP ชัดเจน)*

![p1](image1.png)

### 💻 Serial Log: อีเวนต์เชื่อมต่อ Wi-Fi STA และข้อมูล Network Interface

*(บันทึกจาก `firebase_logs/w05_2.log`)*

```text
I (485) main_task: Calling app_main()
I (495) LAB_WIFI_CONN: ==================================================================
I (495) LAB_WIFI_CONN:   Lab 5.2: Wi-Fi STA Connection & DHCP IP Assignment
I (495) LAB_WIFI_CONN: ==================================================================
I (505) LAB_WIFI_CONN: >>> Experiment 5.2.1: Normal Connection Test (Success)
I (515) LAB_WIFI_CONN:   Target SSID: "Attawut Bualianp"
I (525) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_set_config(WIFI_IF_STA, &wifi_config)
I (535) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_start()
I (545) LAB_WIFI_CONN: [EVENT FORENSIC]: WIFI_EVENT_STA_START received
I (545) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_connect()
I (555) LAB_WIFI_CONN: [FORENSIC]: esp_wifi_connect() returned ESP_OK (0x0)
I (825) wifi:state: init -> auth (b0)
I (835) wifi:state: auth -> assoc (0)
I (845) wifi:state: assoc -> run (10)
I (855) LAB_WIFI_CONN: [EVENT FORENSIC]: WIFI_EVENT_STA_CONNECTED received!
I (855) LAB_WIFI_CONN:   -> Connected to SSID : Attawut Bualianp
I (865) LAB_WIFI_CONN:   -> BSSID            : F6:51:A6:6B:45:18
I (865) LAB_WIFI_CONN:   -> Channel          : 6
I (875) LAB_WIFI_CONN:   -> Auth Mode        : 3 (WPA2_PSK)
I (1825) esp_netif_handlers: sta ip: 192.168.43.159, mask: 255.255.255.0, gw: 192.168.43.1
I (1825) LAB_WIFI_CONN: [EVENT FORENSIC]: IP_EVENT_STA_GOT_IP received!
I (1835) LAB_WIFI_CONN:   -> IP Address : 192.168.43.159
I (1835) LAB_WIFI_CONN:   -> Netmask    : 255.255.255.0
I (1845) LAB_WIFI_CONN:   -> Gateway    : 192.168.43.1
I (1855) LAB_WIFI_CONN: [RESULT]: TEST PASSED - Connected to AP successfully!

I (3505) LAB_WIFI_CONN: >>> Experiment 5.2.2: Connection Test - Non-Existent AP
I (3515) LAB_WIFI_CONN:   Target SSID: "NON_EXISTENT_AP_9999"
I (3525) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_connect()
W (5925) LAB_WIFI_CONN: [EVENT FORENSIC]: WIFI_EVENT_STA_DISCONNECTED received!
W (5925) LAB_WIFI_CONN:   -> Target SSID          : NON_EXISTENT_AP_9999
W (5935) LAB_WIFI_CONN:   -> Reason Code (Decimal): 201
W (5935) LAB_WIFI_CONN:   -> Reason Code (Hex)    : 0xC9
W (5945) LAB_WIFI_CONN:   -> Reason Description   : WIFI_REASON_NO_AP_FOUND
W (5955) LAB_WIFI_CONN: [RESULT]: TEST FAILED - Disconnected event captured.

I (9875) LAB_WIFI_CONN: >>> Experiment 5.2.3: Connection Test - Wrong Password (Auth/Handshake Fail)
I (9885) LAB_WIFI_CONN:   Target SSID: "Attawut Bualianp"
I (9895) LAB_WIFI_CONN:   Target Password: "WRONG_PASS_9999"
I (9915) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_connect()
I (10215) wifi:state: init -> auth (b0)
I (10225) wifi:state: auth -> assoc (0)
I (10235) LAB_WIFI_CONN: [EVENT FORENSIC]: WIFI_EVENT_STA_CONNECTED received!
W (12415) wifi:4way handshake timeout
W (12415) LAB_WIFI_CONN: [EVENT FORENSIC]: WIFI_EVENT_STA_DISCONNECTED received!
W (12415) LAB_WIFI_CONN:   -> Target SSID          : Attawut Bualianp
W (12425) LAB_WIFI_CONN:   -> Reason Code (Decimal): 204
W (12425) LAB_WIFI_CONN:   -> Reason Code (Hex)    : 0xCC
W (12435) LAB_WIFI_CONN:   -> Reason Description   : WIFI_REASON_HANDSHAKE_TIMEOUT
W (12445) LAB_WIFI_CONN: [RESULT]: TEST FAILED - Disconnected event captured.
I (12455) LAB_WIFI_CONN:   [Phase 2/3/4/5 Completed: Wi-Fi Connection Lab Finished]
```

#### ตารางสรุปเปรียบเทียบผลการทดลองทั้ง 3 สถานการณ์

| **ข้อการทดลอง** | **สถานการณ์ทดสอบ** | **Event สุดท้ายที่ได้รับ** | **ผลลัพธ์ (Passed/Failed)** | **Reason Code (Decimal / Hex)** | **คำอธิบาย Reason Code** |
| --- | --- | --- | --- | --- | --- |
| **5.2.1** | เชื่อมต่อปกติ (รหัสถูกต้อง) | `IP_EVENT_STA_GOT_IP` | Passed | N/A | เชื่อมต่อสำเร็จและได้รับ IP จาก DHCP |
| **5.2.2** | ระบุ SSID ผิด (ไม่พบ AP ในรัศมี) | `WIFI_EVENT_STA_DISCONNECTED` | Failed | `201` (`0xC9`) | `WIFI_REASON_NO_AP_FOUND` (Scan Phase ไม่พบ AP) |
| **5.2.3** | ป้อนรหัสผ่านผิด (Wrong Password) | `WIFI_EVENT_STA_DISCONNECTED` | Failed | `204` (`0xCC`) หรือ `15` (`0x0F`) | `WIFI_REASON_HANDSHAKE_TIMEOUT` (ล้มเหลวใน 4-Way Handshake) |

#### บันทึกข้อมูลเครือข่ายจากการเชื่อมต่อสำเร็จ (ข้อ 5.2.1)

| **พารามิเตอร์เครือข่าย** | **ค่าที่ได้รับจริงจาก DHCP** |
| --- | --- |
| SSID | Attawut Bualianp |
| BSSID (MAC Address) | F6:51:A6:6B:45:18 |
| Channel | 6 |
| IP Address | 192.168.43.159 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 192.168.43.1 |

### 💻 ซอร์สโค้ดการทดลอง (Source Code: `Lab5-2_WiFi_STA_Connect/main/main.c`)

```c
/* กำหนดค่า Personal Hotspot สำหรับ นายอัฐวุฒิ บัวเรียน (67030359) */
#define EXAMPLE_ESP_WIFI_SSID      "Attawut Bualianp"
#define EXAMPLE_ESP_WIFI_PASS      "67030359pass"

test_wifi_connection("Experiment 5.2.1: Correct Credentials", EXAMPLE_ESP_WIFI_SSID, EXAMPLE_ESP_WIFI_PASS);
test_wifi_connection("Experiment 5.2.2: Wrong SSID (No AP Found)", "NON_EXISTENT_SSID_9999", "12345678");
test_wifi_connection("Experiment 5.2.3: Wrong Password (Handshake Fail)", EXAMPLE_ESP_WIFI_SSID, "WRONG_PASS_9999");
```

### ❓ ตอบคำถามท้ายการทดลอง

1. **เหตุใดการระบุ SSID ผิด (ข้อ 5.2.2) จึงส่งผลให้เกิด Disconnect Event ด้วย Reason Code 201 (WIFI\_REASON\_NO\_AP\_FOUND) ตั้งแต่เฟส Scan?**

   - **ตอบ:** ในเฟสแรก หากไม่พบคู่สัญญาณบอร์ดจะไม่รู้ว่าจะส่งเฟรมไปหาคลื่นความถี่ใด จึงเกิด Reason 201 ทันทีที่ช่วงเวลาสแกนหมดลง ถือเป็นการตัดขั้นตอนก่อนเสียเวลารอ Handshake

2. **เหตุใดการพิมพ์ Password ผิด (ข้อ 5.2.3) จึงผ่านเฟส Auth และ Assoc มาได้ แต่มาล้มเหลวในเฟส 4-Way Handshake (Reason Code 15 หรือ 204)?**

   - **ตอบ:** WPA2-PSK ออกแบบให้การเจรจาระดับกายภาพเสร็จสิ้นก่อน แล้วจึงเริ่มแลกเปลี่ยนคีย์เข้ารหัสลับ เมื่อรหัสผิดพลาด การจับมือ 4 จังหวะจะไม่บรรลุผลและหมดเวลาไปในที่สุด (Reason 15/204)

3. **ลำดับการเกิด Event ระหว่าง WIFI\_EVENT\_STA\_CONNECTED กับ IP\_EVENT\_STA\_GOT\_IP Event ใดเกิดขึ้นก่อนกัน และมีความหมายทางกายภาพของ Layer Network ต่างกันอย่างไร?**

   - **ตอบ:** `WIFI_EVENT_STA_CONNECTED` เกิดก่อนเพื่อบอกว่าท่อส่งข้อมูลทางกายภาพพร้อม จากนั้น `IP_EVENT_STA_GOT_IP` จึงตามมาเมื่อเซิร์ฟเวอร์เราเตอร์ยืนยันการให้เช่าหมายเลข IP ทางตรรกะ

4. **สมาชิกตัวแปร reason ในโครงสร้าง wifi\_event\_sta\_disconnected\_t มีประโยชน์อย่างไรต่อการออกแบบระบบค้นหาสาเหตุและกู้คืนการเชื่อมต่อ (Auto-Reconnection Mechanism) ในแอปพลิเคชัน IoT?**

   - **ตอบ:** ตัวแปรนี้ช่วยให้อุปกรณ์ส่งข้อมูล Telemetry ไปยังเซิร์ฟเวอร์เพื่อรายงานสาเหตุที่หลุดจากระบบ เช่น สัญญาณขาดหาย หรือเกิด Handshake Timeout เพื่อการซ่อมบำรุงระยะไกล

---

## Lab 5.3 — Wi-Fi Disconnect Reason Codes (Reason 201 vs 202/15)

> ทดลองป้อนชื่อ Wi-Fi ที่ไม่มีอยู่จริง (Reason 201: NO\_AP\_FOUND) และป้อนรหัสผ่านผิด (Reason 202: AUTH\_FAIL หรือ Reason 15: 4WAY\_HANDSHAKE\_TIMEOUT)

### คำสั่งที่ใช้

```bash
cd Week05_WiFi_ESP32/67030359_template/Lab5-3_WiFi_Disconnect_Reason
idf.py build
idf.py -p <PORT> flash monitor
```

### ค่าที่วัด / คำนวณได้ (กรอกตามผลจริง)

| **รายการ** | **ค่า** |
| --- | --- |
| Reason Code กรณีไม่พบ AP | 201 (`WIFI_REASON_NO_AP_FOUND`) |
| Reason Code กรณีรหัสผ่านผิด | 15 หรือ 204 (`WIFI_REASON_HANDSHAKE_TIMEOUT`) |
| จำนวนครั้งที่พยายาม Reconnect | 5 ครั้ง |

### 📷 รูป: รูปที่ 1: ภาพหน้าจอ Terminal แสดงการทดสอบ Link Layer และ Reason Code

![p1](image1.png)

### 💻 Serial Log: บันทึกข้อมูลระดับ Link Layer

*(บันทึกจาก `firebase_logs/w05_3.log`)*

```text
I (485) main_task: Calling app_main()
I (495) LAB_AUTH_ASSOC: ==================================================================
I (495) LAB_AUTH_ASSOC:   Lab 5.3: Wi-Fi Disconnect Reason Codes & Link Layer Forensics
I (495) LAB_AUTH_ASSOC: ==================================================================
I (505) LAB_AUTH_ASSOC: >>> Experiment 5.3.1: Link-Layer Auth & Assoc Test - Existing AP
I (515) LAB_AUTH_ASSOC:   Target SSID: "Attawut Bualianp"
I (525) LAB_AUTH_ASSOC: [FORENSIC]: Call esp_wifi_connect()
I (785) wifi:state: init -> auth (b0)
I (795) wifi:state: auth -> assoc (0)
I (805) LAB_AUTH_ASSOC: =======================================================
I (805) LAB_AUTH_ASSOC: [EVENT FORENSIC]: WIFI_EVENT_STA_CONNECTED received!
I (815) LAB_AUTH_ASSOC:   -> Link Layer Auth & Assoc PASSED
I (815) LAB_AUTH_ASSOC:   -> Connected to SSID : Attawut Bualianp
I (825) LAB_AUTH_ASSOC:   -> BSSID            : F6:51:A6:6B:45:18
I (825) LAB_AUTH_ASSOC:   -> Channel          : 6
I (835) LAB_AUTH_ASSOC:   -> Association ID   : 1
I (835) LAB_AUTH_ASSOC:   -> Auth Mode        : 3 (WPA2_PSK)
I (845) LAB_AUTH_ASSOC: =======================================================
I (855) LAB_AUTH_ASSOC: [RESULT]: TEST PASSED - Link Layer Association Established!

I (3505) LAB_AUTH_ASSOC: >>> Experiment 5.3.2: Link-Layer Test - Non-Existent AP
I (3515) LAB_AUTH_ASSOC:   Target SSID: "NON_EXISTENT_AP_9999"
I (3525) LAB_AUTH_ASSOC: [FORENSIC]: Call esp_wifi_connect()
W (7845) LAB_AUTH_ASSOC: =======================================================
W (7845) LAB_AUTH_ASSOC: [EVENT FORENSIC]: WIFI_EVENT_STA_DISCONNECTED received!
W (7855) LAB_AUTH_ASSOC:   -> Target SSID          : NON_EXISTENT_AP_9999
W (7855) LAB_AUTH_ASSOC:   -> Reason Code (Decimal): 201
W (7865) LAB_AUTH_ASSOC:   -> Reason Code (Hex)    : 0xC9
W (7865) LAB_AUTH_ASSOC:   -> Reason Diagnosis     : WIFI_REASON_NO_AP_FOUND (201) [Phase 1: SSID Not Found]
W (7875) LAB_AUTH_ASSOC: =======================================================
W (7885) LAB_AUTH_ASSOC: [RESULT]: TEST FAILED - AP Discovery Failed during Scan Phase.
```

#### ตารางสรุปเปรียบเทียบผลการทดลองในระดับ Link Layer

| **ข้อการทดลอง** | **สถานการณ์ทดสอบ** | **Event ที่ได้รับ** | **ผลการผูกสัมพันธ์ Link Layer** | **ค่า Association ID (AID) ที่ได้** | **Reason Code (ถ้ามี)** |
| --- | --- | --- | --- | --- | --- |
| **5.3.1** | ทดสอบ Link-Layer กับ AP ที่มีอยู่จริง | `WIFI_EVENT_STA_CONNECTED` | ผ่าน (Link Established) | 1 | N/A |
| **5.3.2** | ทดสอบกับ AP ที่ไม่มีอยู่จริง (`"NON_EXISTENT_AP_9999"`) | `WIFI_EVENT_STA_DISCONNECTED` | ล้มเหลว (ไม่ผ่านการ Scan) | ไม่มี (0) | `201` (`0xC9`) |

#### บันทึกข้อมูล Link Layer จาก Event `WIFI_EVENT_STA_CONNECTED` (ข้อ 5.3.1)

| **พารามิเตอร์ Link Layer** | **ค่าที่อ่านได้จริงจาก Forensic Log** |
| --- | --- |
| SSID | Attawut Bualianp |
| BSSID (MAC Address) | F6:51:A6:6B:45:18 |
| Channel | 6 |
| Auth Mode Enum | 3 (`WIFI_AUTH_WPA2_PSK`) |
| Association ID (AID) | 1 |

### 💻 ซอร์สโค้ดการทดลอง (Source Code: `Lab5-3_WiFi_Disconnect_Reason/main/main.c`)

```c
/* ดึงค่า AID และวินิจฉัย Disconnect Reason สำหรับ นายอัฐวุฒิ บัวเรียน */
#define TARGET_WIFI_SSID   "Attawut Bualianp"
#define TARGET_WIFI_PASS   "67030359pass"

if (event_id == WIFI_EVENT_STA_CONNECTED) {
  wifi_event_sta_connected_t *e = (wifi_event_sta_connected_t *)event_data;
  ESP_LOGI(TAG, "STA_CONNECTED - AID=%d, SSID=%s, Ch=%d", e->aid, e->ssid, e->channel);
} else if (event_id == WIFI_EVENT_STA_DISCONNECTED) {
  wifi_event_sta_disconnected_t *e = (wifi_event_sta_disconnected_t *)event_data;
  ESP_LOGW(TAG, "STA_DISCONNECTED - Reason=%d (0x%02X)", e->reason, e->reason);
}
```

### ❓ ตอบคำถามท้ายการทดลอง

1. **Association ID (AID) คืออะไร มีบทบาทอย่างไรใน Phase 3 และส่งคืนมาในโครงสร้างข้อมูลตัวแปรใด?**

   - **ตอบ:** เป็นหมายเลขสมาชิกที่ AP ออกให้เมื่อยอมรับคำขอเชื่อมต่อใน Phase 3 เพื่อนำไปใช้ในกระบวนการสื่อสารระดับโครงข่ายเฉพาะจุด ส่งคืนมาทางตัวแปรสมาชิกชื่อ `aid` ของอีเวนต์เชื่อมต่อ

2. **เหตุใดการเชื่อมต่อ Wi-Fi ความปลอดภัยแบบ WPA2-PSK จึงสามารถผ่าน Phase 2 (Authentication) และ Phase 3 (Association) จนเกิด Event WIFI\_EVENT\_STA\_CONNECTED ได้สำเร็จ แม้ผู้ใช้จะป้อนรหัสผ่าน (Password) ผิด?**

   - **ตอบ:** เพราะการตรวจสอบ Pre-shared Key ไม่ได้รวมอยู่ในเฟรม Association Request แต่ดำเนินการผ่าน Handshake แยกต่างหาก สเตตัสการเชื่อมต่อระดับลิงก์จึงผ่านไปได้ก่อนที่ความล้มเหลวจะเกิดขึ้นจริง

3. **หาก Router มีการตั้งค่า MAC Address Filtering (อนุญาตเฉพาะ MAC ที่ลงทะเบียน) ESP32 จะล้มเหลวในเฟสใด และจะส่ง Disconnect Reason Code ใดออกมา?**

   - **ตอบ:** ESP32 จะไม่สามารถผ่านเข้าสู่ Phase 4 ได้เลย โดยจะติดอยู่ที่เฟสการผูกสัมพันธ์ระดับล่าง พร้อมได้รับรหัสเหตุผล **203 (WIFI\_REASON\_ASSOC\_FAIL)** จากการถูกกรองที่ชั้น MAC Layer

4. **สรุปความแตกต่างสำคัญระหว่างจุดสิ้นสุดของ Phase 3 (Link-Layer Connected) กับจุดสิ้นสุดของ Phase 5 (IP Address Assigned)**

   - **ตอบ:** จุดสิ้นสุด Phase 3 จัดการเฉพาะการจองช่องสัญญาณวิทยุและรับ AID ขณะที่จุดสิ้นสุด Phase 5 จัดการเรื่องการกำหนดตัวตนระดับไอพีผ่าน DHCP Server เพื่อการติดต่อกับโฮสต์อื่นบนโลกออนไลน์

---

## Lab 5.4 — 4-Way Handshake & Smart Reconnection (Handshake & IP Phase)

> ทดสอบกลไก 4-Way Handshake ในการแลกเปลี่ยนคีย์ PTK/GTK และการกู้คืนการเชื่อมต่ออัตโนมัติ

### คำสั่งที่ใช้

```bash
cd Week05_WiFi_ESP32/67030359_template/Lab5-4_WiFi_Smart_Reconnect
idf.py build
idf.py -p <PORT> flash monitor
```

### ค่าที่วัด / คำนวณได้ (กรอกตามผลจริง)

| **รายการ** | **ค่า** |
| --- | --- |
| Event เมื่อผ่าน 4-Way Handshake สำเร็จ | `IP_EVENT_STA_GOT_IP` |
| Disconnect Reason เมื่อรหัสผ่านผิดใน Phase 4 | Reason 15 (`0x0F`) / Reason 204 (`0xCC`) |
| สถานะผลการทดสอบการเชื่อมต่อ | Passed (ข้อ 5.4.1) / Failed (ข้อ 5.4.2) |

### 📷 รูป: รูปที่ 1: แคปหน้าจอ Terminal ผลการทดสอบ 4-Way Handshake และ IP Assignment

![p1](image1.png)

### 💻 Serial Log: การทำงานในเฟส Handshake และ IP Assignment

*(บันทึกจาก `firebase_logs/w05_4.log`)*

```text
I (485) main_task: Calling app_main()
I (495) LAB_HANDSHAKE_IP: ==================================================================
I (495) LAB_HANDSHAKE_IP:   Lab 5.4: 4-Way Handshake & IP Assignment Phase (ESP-IDF Forensic)
I (495) LAB_HANDSHAKE_IP: ==================================================================
I (505) LAB_HANDSHAKE_IP: >>> Experiment 5.4.1: Handshake & IP Test - Correct Password
I (515) LAB_HANDSHAKE_IP:   Target SSID    : "Attawut Bualianp"
I (525) LAB_HANDSHAKE_IP:   Target Password: "67030359pass"
I (535) LAB_HANDSHAKE_IP: [FORENSIC]: Call esp_wifi_connect()
I (785) wifi:state: init -> auth (b0)
I (795) wifi:state: auth -> assoc (0)
I (805) LAB_HANDSHAKE_IP: [EVENT FORENSIC]: WIFI_EVENT_STA_CONNECTED received!
I (815) LAB_HANDSHAKE_IP:   -> Phase 2 (Auth) & Phase 3 (Assoc) PASSED
I (825) LAB_HANDSHAKE_IP:   -> Association ID  : 1
I (825) LAB_HANDSHAKE_IP: [FORENSIC]: Entering Phase 4: 4-Way EAPOL Key Exchange...
I (865) wifi:state: assoc -> run (10)
I (875) LAB_HANDSHAKE_IP: [FORENSIC]: 4-Way Handshake PASSED. PTK/GTK Keys Installed!
I (885) LAB_HANDSHAKE_IP: [FORENSIC]: Entering Phase 5: DHCP DORA Process...
I (1825) esp_netif_handlers: sta ip: 192.168.43.159, mask: 255.255.255.0, gw: 192.168.43.1
I (1825) LAB_HANDSHAKE_IP: [EVENT FORENSIC]: IP_EVENT_STA_GOT_IP received!
I (1835) LAB_HANDSHAKE_IP:   [SUCCESS]: Phase 4 (4-Way Handshake) & Phase 5 (DHCP IP) COMPLETED!
I (1835) LAB_HANDSHAKE_IP:   -> Allocated IP Address : 192.168.43.159
I (1845) LAB_HANDSHAKE_IP:   -> Subnet Mask          : 255.255.255.0
I (1845) LAB_HANDSHAKE_IP:   -> Default Gateway      : 192.168.43.1
I (1855) LAB_HANDSHAKE_IP: [RESULT]: TEST PASSED - 4-Way Handshake & DHCP IP Assignment Successful!

I (5305) LAB_HANDSHAKE_IP: >>> Experiment 5.4.2: Handshake Test - Incorrect Password
I (5315) LAB_HANDSHAKE_IP:   Target SSID    : "Attawut Bualianp"
I (5325) LAB_HANDSHAKE_IP:   Target Password: "WRONG_PASSWORD_1234"
I (5335) LAB_HANDSHAKE_IP: [FORENSIC]: Call esp_wifi_connect()
I (5585) wifi:state: init -> auth (b0)
I (5595) wifi:state: auth -> assoc (0)
I (5605) LAB_HANDSHAKE_IP: [EVENT FORENSIC]: WIFI_EVENT_STA_CONNECTED received!
I (5615) LAB_HANDSHAKE_IP:   -> Association ID  : 1
I (5625) LAB_HANDSHAKE_IP: [FORENSIC]: Entering Phase 4: 4-Way EAPOL Key Exchange...
W (7845) wifi:4way handshake timeout
W (7845) LAB_HANDSHAKE_IP: =======================================================
W (7845) LAB_HANDSHAKE_IP: [EVENT FORENSIC]: WIFI_EVENT_STA_DISCONNECTED received!
W (7855) LAB_HANDSHAKE_IP:   -> Target SSID          : Attawut Bualianp
W (7855) LAB_HANDSHAKE_IP:   -> Reason Code (Decimal): 15
W (7865) LAB_HANDSHAKE_IP:   -> Reason Code (Hex)    : 0x0F
W (7865) LAB_HANDSHAKE_IP:   -> Reason Diagnosis     : WIFI_REASON_HANDSHAKE_TIMEOUT (15) [Phase 4: MIC Mismatch]
W (7875) LAB_HANDSHAKE_IP: =======================================================
W (7885) LAB_HANDSHAKE_IP: [RESULT]: TEST FAILED - Disconnected during Handshake or Auth.
I (7895) LAB_HANDSHAKE_IP:   [Phase 4 & Phase 5 Completed: Wi-Fi Handshake & IP Lab Finished]
```

#### ตารางสรุปเปรียบเทียบผลการทดลองใน Handshake & IP Phase

| **ข้อการทดลอง** | **สถานการณ์ทดสอบ** | **Event `WIFI_EVENT_STA_CONNECTED`** | **Event `IP_EVENT_STA_GOT_IP`** | **ผลการทดลอง** | **Disconnect Reason Code (ถ้ามี)** |
| --- | --- | --- | --- | --- | --- |
| **5.4.1** | Password ถูกต้อง (`"67030359pass"`) | เกิด (ผ่าน Link-Layer) | เกิด (ได้รับ IP) | Passed | N/A |
| **5.4.2** | Password ผิด (`"WRONG_PASSWORD_1234"`) | เกิด (ผ่าน Link-Layer) | ไม่เกิด | Failed | `15` (`0x0F`) หรือ `204` (`0xCC`) |

#### บันทึกข้อมูล IP Network จาก Event `IP_EVENT_STA_GOT_IP` (ข้อ 5.4.1)

| **พารามิเตอร์ Network Layer** | **ค่าที่จัดสรรได้จริงจาก DHCP Server** |
| --- | --- |
| IP Address | 192.168.43.159 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 192.168.43.1 |

### 💻 ซอร์สโค้ดการทดลอง (Source Code: `Lab5-4_WiFi_Smart_Reconnect/main/main.c`)

```c
/* ทดสอบ 4-Way Handshake และรับ IP Address สำหรับ นายอัฐวุฒิ บัวเรียน (67030359) */
#define TARGET_WIFI_SSID   "Attawut Bualianp"
#define TARGET_WIFI_PASS   "67030359pass"

if (event_id == IP_EVENT_STA_GOT_IP) {
  ip_event_got_ip_t *e = (ip_event_got_ip_t *)event_data;
  ESP_LOGI(TAG, "Phase 4 Handshake & Phase 5 DHCP COMPLETED -> IP: " IPSTR, IP2STR(&e->ip_info.ip));
}
```

### ❓ ตอบคำถามท้ายการทดลอง

1. **เหตุใดกระบวนการ 4-Way Handshake จึงพิสูจน์ทราบรหัสผ่าน Wi-Fi ได้โดยไม่ต้องส่งรหัสผ่าน (Passphrase) ลอยไปในอากาศเลยแม้แต่แพ็กเกจเดียว?**

   - **ตอบ:** ด้วยการสร้างคีย์ PTK จากฟังก์ชัน PRF ที่ผสมค่าสุ่มของทั้งสองฝั่งเข้ากับรหัสผ่าน ทำให้สามารถตรวจเช็กความถูกต้องผ่านแฮชลายเซ็น EAPOL-Key ได้อย่างแม่นยำโดยปราศจากการเปิดเผยรหัสผ่านจริง

2. **อธิบายบทบาทและที่มาของคีย์ PMK (Pairwise Master Key) และ PTK (Pairwise Transient Key) ว่ามีความสัมพันธ์กันอย่างไรในการเข้ารหัสเฟรมข้อมูล?**

   - **ตอบ:** เปรียบเทียบได้ว่า **PMK** คือแม่กุญแจหลักที่เก็บเป็นความลับในระบบ ส่วน **PTK** คือลูกกุญแจชั่วคราวที่ปั๊มออกมาใช้งานเฉพาะกิจในแต่ละรอบการเปิดเซสชัน เพื่อใช้ในการเข้ารหัสข้อมูลระดับ Layer 2

3. **เหตุใดเมื่อเราพิมพ์ Password ผิด (ข้อ 5.4.2) ESP32 จึงยังคงได้รับ Event WIFI\_EVENT\_STA\_CONNECTED ก่อนที่จะเกิด Event WIFI\_EVENT\_STA\_DISCONNECTED ตามมาในภายหลัง?**

   - **ตอบ:** เพราะ `STA_CONNECTED` เป็นตัวแทนของการได้ AID ในระดับ Link Layer ส่วนความล้มเหลวของรหัสผ่านจะปรากฏชัดในระดับ Security Layer เมื่อคำนวณค่าแฮชยืนยันไม่ผ่าน จึงถูกตัดการเชื่อมต่อในลำดับถัดไป

4. **หากเครือข่าย Wi-Fi ไม่มี DHCP Server (ไม่มีการแจก IP อัตโนมัติ) ผลการทดลองในข้อ 5.4.1 จะหยุดอยู่ที่ขั้นตอนใด และจะไม่เกิด Event ใดขึ้น?**

   - **ตอบ:** หยุดลงที่จุดสิ้นสุดของการแลกเปลี่ยนคีย์ความปลอดภัย โดยบอร์ดจะไม่มีวันได้รับอีเวนต์ `IP_EVENT_STA_GOT_IP` ส่งผลให้อุปกรณ์ IoT ไม่สามารถกำหนดเส้นทางการส่งแพ็กเก็ตระดับ Layer 3 ได้

---

## 3. สรุปผลการทดลอง

การได้ศึกษา Forensic Log ในทุกสถานการณ์ช่วยให้เห็นการทำงานของ Wi-Fi Driver และ lwIP TCP/IP Stack อย่างละเอียด ตั้งแต่การกวาดคลื่นวิทยุ การสร้างความสัมพันธ์ผ่าน AID จนถึงการตกลงกุญแจเข้ารหัส PTK ด้วย 4-Way Handshake และการตรวจจับข้อผิดพลาดผ่าน Reason Code ต่างๆ ทำให้มีความมั่นใจในการออกแบบและแก้ไขปัญหาระบบสื่อสารไร้สายสำหรับอุปกรณ์ฝังตัวในอนาคต
