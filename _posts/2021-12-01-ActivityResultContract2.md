---
layout: single
title:  "[Android, Kotlin] ActivityResultContract API (2) 갤러리에서 사진 가져오기"
---


```
class AddImageActivity : AppCompatActivity(){

    //콜백 선언
    private val selectImageFromGalleryResult = registerForActivityResult(ActivityResultContracts.GetContent()){
        it?.let{ uri ->
            //결과값(이미지 uri)으로 이미지 크롭하기
            cropImage(uri)
        }
    }
    
    override fun onCreate(savedInstanceState: Bundle?){
        super.onCreate(savedInstancestate)
        setContentView(R.layout.activity_add_image)
      
        btnSelectImg.setOnClickListener{
            //launch를 사용하여 선언한 콜백을 실행
            selectImageFromGalleryResult.launch("image/*")
        }
    }
}
```
