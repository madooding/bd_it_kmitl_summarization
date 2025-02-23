# Big Data summary (Final)


## What is sqoop?

__Sqoop__ คือเครื่องมือที่ทำงานบน Command line ซึ่งใช้งานได้ง่ายซึ่งเอามาทำอะไรได้หลายๆอย่างดังนี้

1. เอามา import ตาราง หรือ database ทั้งก่้อนลงใน HDFS 
2. Generate class ภาษา Java ที่เอาไว้ใช้สำหรับจัดการกับข้อมูลที่ถูก import เข้ามา
3. เอามา import ฐานข้อมูล SQL ลงใน Hive data warehouse ได้

## ข้อดีของมันน่ะหรือ

- ดึง metadata เอาชนิดข้อมูลของแต่ละ column ใน RDBMS มาใช้ได้
- ใช้ง่าย
- เอามาจัดการการไหลการเปลี่ยนแปลงของข้อมูลได้
- มันใช้ MapReduce ในการ export และ import คือมันดีอ่ะ นั่นแหล่ะ

## สรุปมันคือ? เราเคยเห็นมันที่ไหนมาก่อนหรือเปล่า?

มันคือที่อาจารย์ให้เราดึงข้อมูลใน MySQL นั่นไงล่ะ แล้วเอามาใส่ใน HBASE กับใน Hive อ่ะ __จบ__

## What is flume?

เชิงว่าเอาไว้เก็บข้อมูล log อะไรทำนองนั้น โดยสามารถทำงานได้อย่างต่อเนื่องทำไปเรื่อยๆ อย่างที่เราเอามาเก็บข้อมูลใน __Twitter__ อ่ะ แล้วมันยังเป็น

- Open-source
- น่าเชื่อถือ
- สเกลได้
- จัดการได้ง่าย
- คัสตอมก็ง่าย
- และถูกออกแบบมาเพื่อใช้ในงาน big data อีกด้วย

## What is kafka?

เป็น open-source software เว่ย พัฒนาโดย Apache Software Foundation เขียนโดยใช้ภาษา Scala มันคือระบบที่เอาไว้จัดการส่งข้อมูลแบบ real-time (ที่เราเคยพิมพ์ข้อความไปแล้วเปิดอีก Terminal แล้วมีข้อความส่งมาอ่ะ)

## What is spark?

> มันคือเครื่องมือวิเคราะห์ข้อมูลขนาดใหญ่ที่มีความเร็วดุจดังแสงเลเซอร์ ปิ้วๆ

__Spark__ เป็น Open-source software สำหรับประมวลผล big data ซึ่งมีความเร็วมากๆ ถ้ารันบน disk จะเร็วกว่าเดิม 10 เท่า แต่ถ้ารันบนเมมโมรี่จะเร็วกว่า 100 เท่า เหยดเขขข้ ซึ่งเอามาใช้งานในภาษาโปรแกรมได้หลายภาษาเช่น Scala, Java, Python, SQL, R.

## ทำไมต้องใช้ Spark ด้วยล่ะ

- มันสามารถเอามาจัดการข้อมูลในระดับ Petabytes ได้
- ทำงานเร็วกว่า MapReduce
- มี API ที่ใช้งานง่าย

ซึ่ง Spark เองก็มีหลายแพลตฟอร์มเอาไว้ใช้งานเช่น 
- Spark SQL
- Spark Streaming
- PySpark, SparkR
- MLlib spark.ml
- GraphX

## แล้วเรายังต้องการ Hadoop อยู่ไหม ?

> ต้องการสิ

บางทีเราก็ต้องพี่งพา HDFS YARN และ Services อื่นๆ บน hadoop อย่าง sqoop, flume.

แต่เราก็หาอย่างอื่นมาทดแทนโดยไม่ต้องพึ่งพาสิ่งเหล่านั้นได้ เช่น 
- Spark Standalone
- Amazon S3
- Mesos


## SparkSQL

- __Spark SQL__ คือ module นึงใน Spark สำหรับประมวลผลข้อมูลแบบมีโตรงสร้าง
- __Spark SQL__ รองรับการเขียน SQL ทั้งแบบ ธรรมดาและแบบ HiveQL

## DataFrame

- คือชุดของข้อมูลที่ immutable (แก้ไขไม่ได้) ซึ่งมีรูปแบบเหมือนตารางใน Relational Database

## Jupyter !!!

มันคือสิ่งที่ทำให้เกิด interaction กับการเขียน python ได้ เขียนปุ๊ป แสดงผลลัพธ์ปั๊ป อารมณ์ pyshell

## ต่อไปมาเรื่อง Google Cloud

อะไรที่มีใน Hadoop เนี่ย Gcloud ก็มีเหมือนกัน เช่น

| &nbsp; | Hadoop | Google Cloud |
|------|--------|--------------|
| **Ingestion** |  Sqoop | |
|  | Flume  |  DataFlow |
|  | KafKa  | Pub/Sub  |
| **Storage**   | HDFS  | Google Storage |
|  | HBase/NoSQL  |  Big Table  |
|  | RDBMS  | Cloud SQL  |
| **Data warehouse** | Teradata etc. |  |
| **Big Data Processing**  | Hadoop/Spark | DataProc  |
|  | Jupyter | DataLab  |
|  |  Hive | Big Query |
| **Machine Learning** | Spark MLlib | ML Engine |
| **Data Visiualization** | Tableau etc. | Data Studio |


