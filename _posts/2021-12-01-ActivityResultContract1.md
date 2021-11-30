---
layout: single
title:  "[Android, Kotlin] ActivityResultContract API (1)"
---

### ActivityResultContract API란
> Activity Result를 처리하는 API

카메라같이 메모리를 많이 사용하는 작업의 경우,
결과를 얻는 Activity를 시작할 때, 메모리 부족으로 인해 프로세스와 Activity가 소멸될 수 있음.
-> 콜백을 분리해야함
(Activity를 실행하는 코드와 결과콜백을 분리)

결과 콜백은 프로세스와 Activity를 다시 생성할 때 사용할 수 있어야 하므로
Activity가 생성될 때 마다 콜백을 무조건 등록해야함
//콜백 추가로 공부하기


### registerForActivityResult()
> ActivityResultContract, ActivityResultCallback을 가져와서
다른 Activity을 실행하는 데 사용할 ActivityResultLauncher을 반환함
* ActivityResultContract : 결과를 생성하는 데 필요한 (1)입력 형태와, (2)결과의 출력 형태를 정의함.


### ActivityResultContract 사용하기
1) 콜백을 선언한다
```
val getContent = registerForActivityResult(GetContent()) { uri: Uri? -> 
    //결과 Uri 처리
}
```
registerForActivityResult()는 콜백만 등록하고, Activity을 실행하거나 결과 요청은 하지 않음.
(등록만 한다)


2) launch()를 사용하여 데이터를 받아올 Activity을 실행한다
```
btn.setOnClickListener {
  getContent.launch("image/*")
}
```
입력이 있으면? launch는 ActivityResultContract 유형과 일치하는 입력을 가져온다.
launch()을 호출하면 결과를 생성하는 프로세스가 시작된다.



참고
https://developer.android.com/training/basics/intents/result?hl=ko
