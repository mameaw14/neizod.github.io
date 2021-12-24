---
title: ยังไหว...
tags:
  - Programming
  - Rant
date: 2012-09-17 15:54:00 +0700
---

วันก่อนเจอคำถามงี่เง่าว่า "$1000^{1000}$ กับ $101^{999}$ [\[sic\]][sic] อันไหนมากกว่ากัน?" แล้วก็สำทับท้ายคำถามไว้ว่าห้ามใช้ sense ตอบด้วยนะ

ห้ามใช้ sense ก็กดเครื่องคิดเลขไปสิโว้ย

{: .oversized .figure}
> ![](/images/program/python-integer/versus-of-powers.jpg)
>
> คนตั้งคำถามคงคิดไม่ถึงเนาะ ว่าเครื่องคิดเลขบ้าอะไรจะหาคำตอบของเลขใหญ่ๆ ขนาดนั้นได้

เลยลองเขียนอะไรเล่นๆ เพื่อทดสอบประสิทธิภาพทางการคำนวณตัวเลขดู พบว่าเลขระดับหมื่นหลักก็ยังไหว

{: .oversized .figure}
> ![](/images/program/python-integer/large-fibonacci.jpg)
>
> Fibonacci ลำดับที่ 57075 เมื่อเขียนในฐานสิบจะต้องใช้ตัวอักษร 11928 ตัว

อันที่จริง ด้วย algorithm dynamic programming ง่ายๆ เช่นด้านบนนี้ จะเอาไปใช้คำนวณหา Fibonacci ลำดับที่ห้าล้าน ซึ่งถ้าจะเขียนออกมาในเลขฐานสิบ ต้องใช้ตัวอักษรถึง 1,044,939 ตัวก็ยังไหวนะ (ภายในเวลาประมาณครึ่งนาทีเอง)

ก็อย่าประเมินประสิทธิภาพของคอมพิวเตอร์ต่ำไปละกัน 😈


[sic]: //en.wikipedia.org/wiki/Sic