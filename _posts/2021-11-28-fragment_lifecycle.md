---
layout: single
title:  "[Android, Kotlin] Fragment의 Lifecycle (1)"
---

### Fragment Lifecycle
생명주기 상태
- INITIALIZED
- CREATED
- STARTED
- RESUMED
- DESTROYED

Fragment에는 lifecycle가 있고 
Fragment의 view에도 별도의 lifecycle가 있다


### Fragment의 Lifecycle

### Fragment View의 Lifecycle
> getViewLifecycleOwner() 또는 getViewLifecycleOwnerLiveData()를 사용하여 접근할 수 있는 View에 대한 LifecycleOwner를 유지한다
> getViewLifecycleOwner() 또는 getViewLifecycleOwnerLiveData()를 사용하여 View Lifecycle에 접근할 수 있다


참고
https://developer.android.com/guide/fragments/lifecycle
