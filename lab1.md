# การทดลองที่1 เรื่องการเขียนโปรเเกรมเพื่อรันบนไมโครคอนโทรเลอร์

## วัตถุประสงค์
1. เพื่อทราบการใช้คำสั่งต่างๆ ที่จะรันโปรแกรม 
2. เพื่อทราบข้อมูลพื้นฐานของไมโครคอนโทรเลอร์ที่ใช้ในการทดลอง

## อุปกรณ์ที่ใช้
1. อุปกร์ต่อ usb
2. ไมโครคอลโทรเลอร์ ESP-01
3. เสาอากาศสำหรับไวไฟ
4. คอมพิวเตอร์
## ศึกษาข้อมูลเบื้องต้น
1. 01 run example 1 : https://www.youtube.com/watch?v=NLIUsWLEpmg
2. src code ของโปรแกรม 01_Serial-Monitor : https://github.com/choompol-boonmee/lab63b/blob/master/examples/01_Serial-Monitor/src/main.cpp
3. platformio : https://platformio.org/

## วิธีการทำทดลอง
1. ต่อไมโครคอนโทรเลอร์เข้ากับซีเรียล
2. เข้าcommand prompt
3. เข้าตัวอย่างโปรแกรมจากโดยใช้พิมพ์คำสั่ง **cd pattani** ในหน้า command prompt
4. เลือกตัวอย่างโปรแกรมคำสั่ง **cd 01_Serial-Monitor**
5. พิมพ์คำสั่ง **vi src/main.cpp** เมื่อกด Enter จะขึ้นข้อมูลดังนี้
```c
#include <Arduino.h>

int cnt = 0;

void setup()
{
	Serial.begin(115200);
}

void loop()
{
	cnt++;
	Serial.printf("PATTANI :%d\n",cnt);
	delay(1000);
}
```
6. พิมพ์คำสั่ง vi platformip.ini จะได้ 
```
; IOT for KIDS
;
; By Dr.Choompol Boonmee
; 
[env:exercise01]
platform = nordicnrf51
board = NRF51822
framework = Mbed	
board_build.flash_mode = dout
upload_port = /dev/cu.usbserial-1420
;upload_port = COM3
monitor_port = /dev/cu.usbserial-1420
;monitor_port = COM3
monitor_speed = 115200
```
7. ใช้คำสั่ง **pio run -t upload** เพื่ออัพโหลดโปรแกรมลงในไมโครคอนโทรนเลอร์
8.  กดปุ่มสีดำบนไมโครคอนโทรเลอร์เพื่อให้ดาวโหลด และกดปุ่มรีเซ็ตสีแดงเพื่อรีเซ็ตคำสั่ง
9. ใช้คำสั่ง**pio device monitor** เพื่อดูผลลัพธ์

## การบันทึกผลการทดลอง

- ตัวแปรเคาท์ที่เริ่มจาก 0 ถูกเพิ่มขึ้นทีละ 1 และแสดงผลทุกๆ 1 วินาที และเมื่อลองกดปุ่มรีเซ็ตสีแดง โปรแกรมจะเริ่มนับหนึ่งใหม่อีกครั้ง 
- ![image](https://user-images.githubusercontent.com/80879585/111973695-5aebe700-8b31-11eb-9580-11f89b36df30.png)

## อภิปรายผลการทดลอง
- จากการทดลองนี้พบว่า เมื่อเราทำการลองโปรแกรม 01_Serial-Monitor ลงในบอร์ด ESP-01 แล้วจากนั้นทำการรันเพื่อทดสอบ โปรแกรมจะเริ่มนับจากศูนย์เพิ่มขึ้นทีละหนึ่งไปเรื่อยๆ ซึ่งสามารถสรุปได้ว่าเราสามารถรันโปรแกรมบนบอร์ด ESP-01 ได้

## คำถามหลังการทดลอง

ในขั้นตอนการทดสอบการรันโปรแกรม หากต้องการให้โปรแกรมเริ่มนับหนึ่งใหม่ควรปฏิบัติอย่างไร 
  - ตอบ กดปุ่มรีเซ็ตบนไมโครคอลโทรลเลอร์
  
จากตัวอย่างโปรแกรม ***01_Serial-Monitor*** ตัวแปรเคาท์จะแสดงผลทุกๆกี่วินาที
  - ตอบ แสดงผลทุกๆ 1 วินาที 
