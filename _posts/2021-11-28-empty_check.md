---
layout: single
title:  "[Android, Kotlin] Empty vs Blank 차이점"
---

헷갈려서 정리

### 1. Empty란
null또는 문자열 길이가 0인지 체크함

ex1)
val str = "1234"
str.isEmpty() //false

ex2)
val str2 = ""
str2.isEmpty() //true

ex2)
val str3 = "  "
str3.isEmpty() //false : 공백도 길이로 계산


### 2. Blank란
empty와 다르게 공백도 체크함

ex1)
val str4 = "   "
str4.isEmpty() //true : 공백은 계산하지 않음

val str5 = ""
str5.isEmpty() //true

