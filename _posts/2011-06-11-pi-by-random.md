---
title: หาค่า $\pi$ ด้วยการสุ่ม
tags:
  - Pi
  - Mathematics
  - Probability
  - Randomness
date: 2011-06-11 20:30:00 +0700
origin:
  - name: JuSci
    url: //jusci.net/node/1893
---

$\pi$ (พาย) เป็นค่าคงที่ทางคณิตศาสตร์ที่ไม่มีใครไม่รู้จัก เราท่องกันมาตั้งแต่เด็กๆ ว่าค่า (ประมาณ) ของมันคือ $22/7$ ถ้าใครได้เรียนต่อในสายวิทย์ก็อาจเคยผ่านตาค่าพายที่ละเอียดมากขึ้น อย่าง $3.14159\,26535\,\dots$

และเนื่องจากว่าพายเป็นจำนวนอตรรกยะ ($\pi\in\mathbb{R}\setminus\mathbb{Q}$) ซึ่งไม่สามารถเขียนให้อยู่ในรูปเศษส่วนของจำนวนเต็ม $a/b$ ได้ การหาค่าพายให้แม่นยำได้ซัก 100 ตำแหน่งจึงเป็นเรื่องจำเป็น (และการหาให้ละเอียดกว่านั้นก็ถือเป็นงานอดิเรกของนักคณิตศาสตร์-คอมพิวเตอร์ก็ว่าได้)

เรามีเทคนิคมากมายในการหาค่าพาย แต่ก็ดูจะไม่มีวิธีไหนที่ประหลาดไปกว่าการหาค่าพายด้วย[การสุ่มแบบ Monte Carlo][monte carlo] อีกแล้วครับ

การหาค่าพายด้วยวิธี Monte Carlo นี้เริ่มด้วยแนวคิดง่ายๆ คือการสังเกตความสัมพันธ์ของพื้นที่วงกลมกับสี่เหลี่ยมจตุรัส ดังนี้

$$ \begin{align}
                           \text{Circle Area} &= \pi r^{2} \\
                           \text{Square Area} &= \left(2 r\right)^{2} \\
\frac{\text{Circle Area}}{\text{Square Area}} &= \frac{\pi}{4}
\end{align} $$

แต่เนื่องจากว่า การหาพื้นที่รูปวงกลมด้วยวิธีธรรมดาทั่วไปนั้น ต้องอาศัยค่าพายเข้าช่วยทุกวิธี ตอนนี้แหละที่เราจะใช้วิธีการสุ่มพล๊อตจุดเข้าไปในพื้นที่สี่เหลี่ยมจตุรัส (เสมือนการระบายสีให้พื้นที่) แล้วดูว่าจุดนั้นอยูในพื้นที่วงกลมด้วยหรือไม่ โดยใช้ขั้นตอนวิธีดังนี้

$$ \begin{align}
1:  & \mathbf{\text{procedure}}\;\;\text{pi}\left(\text{int}\;\; n\right) \\
    & \mathbf{\text{begin}} \\
    & \quad\quad \mathbf{\text{var}}\;\; c:=0 \\
    & \quad\quad \mathbf{\text{for}}\;\; i:=1\;\;\mathbf{\text{upto}}\;\; n\;\;\mathbf{\text{do}} \\
5:  & \quad\quad\quad\quad \text{random}\;\; x_{ i}, y_{ i}\in\begin{bmatrix}-1\text{,}1\end{bmatrix} \\
    & \quad\quad\quad\quad \mathbf{\text{if}}\;\;\sqrt{ x_{ i}^{2}+ y_{ i}^{2}}\leq1\;\;\mathbf{\text{then}} \\
    & \quad\quad\quad\quad\quad\quad c\leftarrow c+1 \\
    & \quad\quad\quad\quad \mathbf{\text{end if}} \\
    & \quad\quad \mathbf{\text{end for}} \\
10: & \quad\quad \mathbf{\text{return}}\;\;4\times\frac{ c}{ n} \\
    & \mathbf{\text{end}}
\end{align} $$

ด้วยความก้าวหน้าของเทคโนโลยีคอมพิวเตอร์ในปัจจุบัน ทำให้เราสามารถสุ่มเลขเป็นจำนวนหลายล้านครั้งได้ในไม่กี่อึดใจ และให้ผลลัพท์ค่าพายที่เชื่อถือได้มาประมาณ 2-3 ตำแหน่ง

ทั้งนี้ พึงระลึกไว้ว่าตัวแปรที่สำคัญคือ

การสุ่มต้องเป็นแบบ uniform distribution คือค่าทุกค่ามีโอกาสออกเท่ากัน และไม่มีรูปแบบการออกที่ตายตัว ซึ่งต่างจากการสุ่มแบบ pseudo random ที่มีชุดตัวเลขเตรียมไว้อยู่แล้ว ความแม่นยำในการวัด (จำนวนเลขทศนิยม) จะเป็นตัวกำหนดความละเอียดของผลลัพท์
เพียงเท่านี้ เราก็จะได้ค่าพายด้วยวิธีการที่ไม่น่าเชื่อว่าจะให้ค่าพายออกมาได้ อย่างการสุ่มแบบ Monte Carlo แล้วครับ


[monte carlo]: //en.wikipedia.org/wiki/Monte_Carlo_method