#การทดลองที่1 เรื่องการเขียนโปรเเกรมเพื่อรันบนไมโครคอนโทรเลอร์

## วัตถุประสงค์
1. เพื่อทราบการใช้คำสั่งต่างๆ ที่จะรันโปรแกรม 
2. เพื่อทราบข้อมูลพื้นฐานของไมโครคอนโทรเลอร์ที่ใช้ในการทดลอง

## อุปกรณ์ที่ใช้
1. อุปกร์ต่อ usb
2. ไมโครคอลโทรเลอร์ ESP-01
3. เสาอากาศสำหรับไวไฟ

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
javascript
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
            
6. พิมพ์คำสั่ง **vi platformio.ini** เมื่อกด Enter จะขึ้นดังรูปนี้
      
      
      
      
      
      ![image](https://user-images.githubusercontent.com/80879772/111911794-83c09d80-8a99-11eb-8f0f-918b05017da2.png)

7. อัพโหลดโปรแกรมเข้าไมโครคอนโทรเลอร์ด้วยคำสั่ง **pio run -t upload** เมื่อกด Enter จะขึ้นดังรูปนี้






     ![image](https://user-images.githubusercontent.com/80879772/111912103-bfa83280-8a9a-11eb-903c-06a83b5ec517.png)

8. กดปุ่มรีเซตที่ตัวไมโครคอนโทรเลอร์
9. **pio device monitor** เพื่อดูผลลัพท์


      
      ![image](https://user-images.githubusercontent.com/80879772/112034335-f2245f00-8b70-11eb-9e68-d67d1945da5d.png)



## การบันทึกผลการทดลอง

จากการใช้คำสั่ง vi platformio.ini ทำให้เราได้ทราบข้อมูลดังนี้
1. เป็น paltform ของ espressif8266                   
2. bord ชื่อ esp01_1m
3. ใช้วิธีการเขียนโปรแกรมแบบ arduino
4. port ใช้ของ windows เพราะขึ้นว่า com3

จากการใช้คำสั่ง pio device monitor 
1. จะเห็นว่าตัวแปร count จะเพิ่มขึ้นๆ ทุก 1 วินาที 
2. เมื่อกดปุ่มรีเซตที่ตัวไมโครคอนโทรเลอร์ ก็จะเริ่มนับหนึ่งใหม่
## อภิปรายผลการทดลอง
จากการใช้คำสั่ง vi src/main.cpp ทำให้เราทราบว่าโปรแกรม 01_Serial-Monitor มี2 ส่วน ดังนี้
1. ส่วน set up 
2. ส่วน loop
      ที่จะเพิ่มตัวแปร count และแสดงผลของตัวแปรโดยมีการหน่วงเวลา 1000 ms 
โดยจากการทดลองการเขียนโปรแกรมเพื่อรันบนไมโครคอนโทรเลอร์จะเห็นว่าเมื่อเราอัพโหลดโปรแกรม 01_Serial-Monitor ลงในตัวไมโครคอนโทรเลอร์เรียบร้อยแล้ว และใช้คำสั่ง **pio device monitor** เพื่อดูการทำงานของไมโครคอนโทรเลอร์ ซึ่งหน้าจอจะขึ้นว่ามีการเปลี่ยนตัวแปรทุกๆ 1 วินาที ตามโปรแกรมที่เราได้อัพโหลดลงไป 

## คำถามหลังการทดลอง
