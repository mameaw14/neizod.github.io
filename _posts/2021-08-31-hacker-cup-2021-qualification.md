---
title: Hacker Cup 2021 รอบคัดเลือก
tags:
  - Competitive Programming
  - Facebook Hacker Cup
  - Python
date: 2021-08-31 23:39:42 +0700
---

ลืมไปแล้วว่ามีแข่งเขียนโปรแกรมรายการนี้ด้วย จนกระทั่ง [@jittat][] ทักมาในชั่วโมงสุดท้าย เลยรีบเขียนรีบส่งไปได้แค่เคสง่ายๆ 2 ข้อ 😂


## Consistency

ด้วยความตื่นเต้นที่มีเวลาน้อยนิด เลยคิดออกแค่เคสง่าย A1 (หรือจะเรียกว่าไม่ได้คิดเลยดีกว่า) เพราะเราก็แค่ brute force ลองเปลี่ยนตัวอักษรทุกตัวในคำที่นำเข้ามา ไปเป็นตัวอักษรแต่ละตัวทั้ง 26 แบบในภาษาอังกฤษเลยก็พอ

``` python
ALPHABETS = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
VOWELS = set('AEIOU')

def cost(a, b):
    if a == b:
        return 0
    if (a in VOWELS) ^ (b in VOWELS):
        return 1
    return 2

def min_cost(text):
    return min(sum(cost(a, b) for b in text) for a in ALPHABETS)

for case in range(int(input())):
    text = input().strip()
    print(f'Case #{case+1}: {min_cost(text)}')
```


## Xs and Os

เช่นเดียวกับข้อแรก brute force ไปเลย ด้วยความกลัวนับพลาดจัดๆ เลยเก็บข้อมูลเป็นเซตของเซตของตำแหน่งที่ต้องเติมตัว X ลงไปเพื่อให้ชนะเลย เวลา iterate แต่ละแถว/หลักแล้วก็โยนเซตของตำแหน่งต่างๆ เพิ่มเข้าไป แบบนี้ถึงแม้คำตอบย่อยจะซ้ำกันแต่เราไม่นับซ้ำแน่ๆ 😅

``` python
from collections import defaultdict

def transpose(grid):
    return [list(row) for row in zip(*grid)]

def xwin(grid):
    feasible = defaultdict(set)
    for i, row in enumerate(grid):
        if 'O' in row:
            continue
        moves = frozenset((i,j) for j, v in enumerate(row) if v == '.')
        feasible[len(moves)] |= {moves}
    for j, col in enumerate(transpose(grid)):
        if 'O' in col:
            continue
        moves = frozenset((i,j) for i, v in enumerate(col) if v == '.')
        feasible[len(moves)] |= {moves}
    return feasible

for case in range(int(input())):
    grid = [list(input().strip()) for _ in range(int(input()))]
    feasible = xwin(grid)
    if not feasible:
        answer = 'Impossible'
    else:
        minimum = min(feasible)
        different = len(feasible[minimum])
        answer = f'{minimum} {different}'
    print(f'Case #{case+1}: {answer}')
```

เซ็งนิดหน่อยที่โจทย์ Facebook มันอ่านทำความเข้าใจค่อนข้างยากมากๆ สงสัยเพราะแทนที่จะอธิบายโจทย์แบบที่คนทั่วไปทำกัน (เทียบกับชีวิตจริง, ยกเคสง่าย) แต่กลับเขียนโจทย์ด้วยภาษาคณิตศาสตร์ตั้งแต่ต้น พออ่านแล้วมันไม่ลื่นแปลกๆ ... หรือไม่งั้นก็ต้องอ่านแบบงงๆ จนจบไปก่อนแล้วย้อนอ่านอีกทีเอา


[@jittat]: //twitter.com/jittat
