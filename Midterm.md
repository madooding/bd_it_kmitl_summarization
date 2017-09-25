# Big data summary

> We are forcasting the future based on the past

## การมาของ Big data นั้นได้เริ่มขึ้นแล้ว

เราต้องการเทคโนโลยีใหม่ๆ ล้ำๆ
1. เนื่องจากขนาดของข้อมูลนั้นมันใหญ่มาก
2. RDBMS นั้นก็ห่วย
3. ไม่ใช่ทุกข้อมูลนั้นจะต้องการ ACID เสมอไป (Atomicity, Consistency, Isolation, Durability)
4. หลายๆข้อมูลนั้นไม่มีโครงสร้างตายตัว (Image, Audio)

## อะไรคือ Hadoop ?

ระบบที่ Scalable fault-tolerant distributed สำหรับเก็บข้อมูลและประมวลผล ซึงถูกเขียนด้วยภาษา Java เป็น Open source ภายใต้ Apache license

## Hadoop Environment
จะประกอบไปด้วย

1.  ชั้นของการคำนวณ ซึ่งใช้ framework นึงเรียกว่า MapReduce

2. ชั้นของการเก็บข้อมูล (Filesystem) เรียกว่า HDFS Provides storage

3. ชั้นของ Server cloud เป็น hardware ที่ใช้ run hadoop นั่นเอง

![Hadoop Environment](https://github.com/madooding/bd_it_kmitl_summarization/blob/master/images/hadoop-environment.png)

## HBase คืออะไร ?

HBase เป็น open source software ตัวนึง ซึ่งเป็น distributed database modeled หลังจากมี Google's BigTable ซึ่งก็ถูกเขียนขึ้นโดยใช้ภาษา Java ถูกพัฒนาให้เป็นส่วนนึงของ Hadoop project นั่นแหล่ะ และรันอยู่บน HDFS อีกทีนึง (ทำงานเหมือนกันกับ BigTable)

## HBase features
- Column oriented AKA hadoop database
- สนับสนุนการทำงานแบบ realtime CRUD ด้วย (ซึ่งต่างจาก HDFS)
- ไม่มี SQL Database
- Opensource
- Run on a cluster.

## ใช้ HBase ตอนไหน ?
- ก็เมื่อมีปริมาณของข้อมูลที่จะเอามาเก็บเยอะมาก
- ข้อมูลที่ไม่มีโครงสร้าง (รูปภาพ, เสียง)
- ข้อมูลหรอมแหรม
- ข้อมูลที่เป็นคอลัมน์ๆ
- เมื่อต้องการความยืดหยุ่นสูง

## Data Processing Technology ตัวไหนบ้างที่ใช้ Hadoop

- MapReduce
- Hive
- Pig
- Impala
- Drill
- Spark

## อะไรคือ MapReduce วะ (อ่านมาตั้งนาน เพิ่งจะมาสงสัย)

**MapReduce** นั้นคือรูปแบบการเขียนโปรแกรมอย่างนึงนั่นแหล่ะ มีไว้สำหรับประมวลผลและสร้างเดต้าเซ็ทขนาดใหญ่ด้วยการทำงานแบบ  Parallel algorithm แบบกระจายตัวบนคลัสเตอร์

MapReduce นั้นประกอบไปด้วยเมธอด Map() และ Reduce() ซึ่งรันบน Batch mode

## Hive คืออะไร ?

**Hive** พัฒนาขึ้นโดย Facebook ออกแบบมาเพื่อให้ง่ายต่อการสรุปข้อมูล การดึงข้อมูลแบบชั่วคราวและวิเคราะห์ข้อมูลที่มีปริมาณมากๆ

ซึ่งมันก็มีภาษาสำหรับ query ง่ายๆที่เรียกว่า **HiveQL** ซึ่งพื้นฐานก็มาจาก SQL นั่นแหล่ะ

มันไม่ได้ถูกออกแบบมาเพื่อจัดการกับ Transaction แบบออนไลน์นะแจ๊ะ แล้วก็ไม่แนะนำให้นำมา query ข้อมูลแบบ real-time ด้วย