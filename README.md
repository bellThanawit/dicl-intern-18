### DICL Internship Program 2018

สวัสดีน้องๆที่ให้ความสนใจมาฝึกงานที่บริษัท ดิจิตอล อินไซด์เดอร์ จำกัด ในปี 2018 นี้ทุกๆคนนะครับ ก่อนที่จะเข้ามาฝึกงานกับเรา พี่มีบททดสอบเล็กน้อยเพื่อวัดทักษะพื้นฐานสำหรับนักพัฒนา Mobile Developer น้องๆไม่จำเป็นต้องตอบหรือต้องรู้ทุกเรื่องในบททดสอบนี้ เพราะเรามาสามารถมาเรียนรู้กันภายหลังได้ เพียงแต่เราอยากให้น้องๆทุกคนลองทำด้วยตัวเอง ค้นคว้าเอง ทั้งหมดก็เพื่อประโยชน์ของตัวน้องๆเองและบริษัท หากใครสนใจส่งคำตอบกันมานะได้เลยนะครับ ปิดรับสมัครวันที่ 8 เมษายน 18 เวลา 23:59 น.

## 1. Code in Swift or Java / Kotlin
แบบทดสอบนี้จะดูทักษะความรู้ความเข้าใจเกี่ยวกับเรื่อง Collection เช่น Array, Dictionary เป็นต้น

ดาวน์โหลดข้อมูล [data.json](https://github.com/memogames/dicl-intern-18/blob/master/data.json) และเขียนโค้ดเพื่อหาคำตอบ
- 1.1 หาคะแนนเฉลี่ย **score** ของนักเรียน
- 1.2 แสดงชื่อและเกรดของนักเรียนที่ได้คะแนนมากว่า 70 ขึ้นไป
- 1.3 ค้นหาชื่อนักเรียนที่มีคะแนนมากที่สุดและต่ำที่สุด **score**

คำตอบ:
```
import java.io.FileNotFoundException;
import java.io.FileReader;
import org.json.simple.JSONArray;
import org.json.simple.JSONObject;
import org.json.simple.parser.JSONParser;

public class Score {
    public static void main(String[] args) {
        JSONParser parser = new JSONParser();
        
        try {
            JSONArray arr = (JSONArray) parser.parse(new FileReader("C:\\Users\\dicl-intern-18-master\\data.json"));
            
            long total= 0,max = -999, min = 999;
            
            //1.1
            for (Object o : arr) {
                JSONObject student = (JSONObject) o;
                long Score = (long) student.get("score");
                total+=Score;
            }
            System.out.println(" 1.1: \n Average = " + (total/6)); 
            
            System.out.println("\n 1.2:"); 
            for (Object o : arr) {
                JSONObject student = (JSONObject) o;
                String Name = (String) student.get("name");
                long Score = (long) student.get("score");   
                
                //1.2
                if(Score>70) {
                	System.out.println("Name:" + Name + "\tScore:"+Score);
                }
                
                //1.3
                if(Score>max) {
                	max=Score;        	
                }if(Score<min) {
                	min=Score;
                }                             
            }
            
            System.out.println("\n 1.3: "); 
            System.out.println("Max:" +max);  
            System.out.println("Min:" +min);  
            
        }
        catch(FileNotFoundException fe){
            fe.printStackTrace();
        }
        catch(Exception e){
            e.printStackTrace();
        }
    }
}


```

## 2. Create Simple Mobile Application

แบบทดสอบนี้จะดูทักษะความรู้ความเข้าใจสำหรับการพัฒนาแอปพลิเคชั่น และการใช้ UI พื้นฐานของแต่ละ Platform

### Features
- GET ข้อมูล JSON จาก [movie.json](https://github.com/memogames/dicl-intern-18/blob/master/movie.json)
- แสดงรายชื่อและรูปภาพใน ListView หรือ TableView
- ผู้ใช้สามารถกดเพื่อดูข้อมูลรายละเอียดได้ในหน้าถัดไป
- ผู้ใช้สามารถแชร์ข้อมูลชื่อหนังที่สนใจให้กับเพื่อนๆได้
- ออกแบบ UI ได้ตามความต้องการ
- ใช้ Library เพิิ่มเติิมได้

### Technical
- ดาวน์โหลดข้อมูล JSON
- เครื่องมือที่ใช้ Android Studio หรือ Xcode.

## 3. Tiny Question

Q1: Firebase คืออะไร มีฟังก์ชั่นที่น้องๆชื่นชอบนอะไรบ้างและเพราะอะไร (อย่างน้อย 3 ฟังก์ชั่น)

```
A1:Firebase คือ Project ที่ถูกออกแบบมาให้เป็น API และ Cloud Storage สำหรับพัฒนา Realtime Application รองรับหลาย Platform
ชื่อชอบ firbase storage เป็นบริการพื้นที่เก็บข้อมูล เอาไว้เก็บภาพ วิดีโอ หรือไฟล์ขนาดใหญ่ ยังใช้งาน firbase ไม่มากจึกยังไม่ค่อยรู้ฟังก์ชันต่างๆมาก
```

Q2: REST API คืออะไร

```
A2:คือวิธีในการสร้าง Web Service รูปแบบนึงที่อาศัย HTTP Method (GET, POST, PUT, DELETE) ในการทำงาน และส่งผลกลับมาในรูปแบบของ JSON หรือ XML ส่งผลให้สามารถรับส่งข้อมูลไปมาข้าม Platform ได้อย่างสะดวกมาก
```

Q3: หากต้องสร้างแอปพลิเคชั่น 1 ตัว เพื่อให้รองรับทั้งระบบ iOS และ Android วิิธีไหนที่น้องๆอยากเลือกใช้พัฒนาระหว่าง Native App กับ Cross Platform และเพราะอะไร 

```
A3:เลือก Cross Platform หรือ Hybrid App เพราะ สามารถแปลงไป platform อื่น ๆ ได้โดยง่าย แต่หากเราต้องการพัฒนาแอพฯ ให้มีประสิทธิภาพสูง สามารถเข้าถึงฟังก์ชั่นการทำงานของแต่ละ Platform ได้เต็มที่ ก็ควรเลือกใช้การเขียนแอพฯ แบบ native 
```

Q4: ถ้าให้เลือกได้ 1 บ้าน น้องๆอยากอยู่บ้านไหนระหว่าง Apple , Google และ Microsoft

```
A4:Google
```

Q5: เวลาว่างสิ่งที่ชอบทำที่สุดคืออะไร 2 อันดับแรก

```
A5:ดูหนัง,เล่นเกม
```

Q6: แอปพลิเคชั่นไหนบนมือถือที่ชอบที่สุดและเกียจที่สุดตั้งแต่เคยใช้งานมา (ไม่รวมเกมส์) เพราะอะไร

```
A6:ชอบที่สุดคือ Ture wallet เพราะใช้งานสะดากสามารถโอนเงินได้ง่าย
   และเกียจที่สุดคือ KTB netbank เพราะใช้งานยากไปไม่สะดวกต่อการใช้งาน
```

Q7: อะไรบ้างที่น้องๆคาดว่าจะได้รับในขณะที่ฝึกงานกับพวกเรา?

```
A7: 1.ประสบการณ์การทำงานร่วมกับคนหมู่มาก
    2.ความรู้และเทคนิคใหม่ๆในการทำงาน
    
```

## Submitting

ให้น้องๆ fork repo นี้แล้วตอบคำถาม จากนั้นส่ง repo มาที่ อีเมลล์ memo.games@gmail.com
