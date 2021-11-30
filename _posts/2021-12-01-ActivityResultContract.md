---
layout: single
title:  "[Android, Kotlin] ActivityResultContract API"
---

> Activity Result를 처리하는 API

카메라같이 메모리를 많이 사용하는 작업의 경우,
결과를 얻는 Activity를 시작할 때, 메모리 부족으로 인해 프로세스와 Activity가 소멸될 수 있음.
-> 콜백을 분리해야함
(Activity를 실행하는 코드와 결과콜백을 분리)

결과 콜백은 프로세스와 Activity를 다시 생성할 때 사용할 수 있어야 하므로
Activity가 생성될 때 마다 콜백을 무조건 등록해야함
* 콜백 추가로 공부하기


```
val getContent = registerForActivityResult(GetContent()) { uri: Uri? ->
    //결과 Uri 처리
}
```

참고
https://developer.android.com/training/basics/intents/result?hl=ko
