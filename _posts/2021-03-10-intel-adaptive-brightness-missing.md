---
title: Intel ทำ Adaptive Brightness หาย 😡
tags:
  - Windows
date: 2021-03-10 18:09:22 +0700
---

ไม่รู้ว่าปัญหานี้เกิดขึ้นกับโน๊ตบุ๊คโมเดลไหนบ้าง (แต่เกิดแน่ๆ เพราะมีคน[บ่น][community intel]เยอะ) แถม Intel ยังเลิกทำแอพ Graphics Control Panel ที่มันยังใช้งานได้ดี แล้วเปลี่ยนไปสร้างแอพ Graphics Command Center ขึ้นมาใหม่แต่ต้นแทนอีก ระดับความไม่ใส่ใจผู้ใช้งานเดิมน่าจะไม่วอนตีนโดนด่ามากพอ เลยทำของใหม่แบบลวกๆ จนส่วนตั้งค่า adaptive brightness ทำงานไม่ได้ อวดฉลาดปรับแสงหน้าจอทั้งที่ไม่ได้ขอจนเราปวดตาไปเลยละกัน 🙄

สุดท้ายถ้าอยากแก้ปัญหาก็ต้องลงไปแก้เองที่ระดับ register ของ Windows โชคดีหน่อยมีคนทำเป็น [batch file][] ไว้ให้แล้ว ดับเบิลคลิกทีเดียวพร้อม reboot เครื่องก็หมดปัญหาเลย 🙏



[community intel]: //community.intel.com/t5/Graphics/Intel-Display-Power-Saving-Technology-will-not-stay-disabled/m-p/652802
[batch file]: //github.com/orev/dpst-control