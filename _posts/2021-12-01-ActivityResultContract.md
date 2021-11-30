---
layout: single
title:  "[Android, Kotlin] ActivityResultContract API"
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


```
val getContent = registerForActivityResult(GetContent()) { uri: Uri? ->
    //결과 Uri 처리
}
```

### registerForActivityResult()
> ActivityResultContract, ActivityResultCallback을 가져와서
다른 Activity을 실행하는 데 사용할 ActivityResultLauncher을 반환함

1) ActivityResultContract : 결과를 생성하는 데 필요한 (1)입력 유형과, 결과의 (2)출력 유형을 정의함.
사진 촬영, 권한 요청 과 같은 기본 인텐트 작업의 기본 계약을 제공함.
자체 맞춤 계약을 만들 수도 있음.

2) ActivityResultCallback : ActivityResultContract에 정의된 '출력 유형'의 객체를 가져오는 
onActivityResult() 메서드가 포함된 인터페이스이다.


여러 Activity 결과 호출이 있다면
registerForActivityResult()을 여러번 호출하여
여러개의 ActivityResultLauncher 인스턴스를 등록할 수 있다.




참고
https://developer.android.com/training/basics/intents/result?hl=ko
