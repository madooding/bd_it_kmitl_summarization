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