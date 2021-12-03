---
layout: single
title:  "[Android, Kotlin] ActivityResultContract API (2) 갤러리에서 사진 가져오기"
---


```
class AddImageActivity : AppCompatActivity(){

    //
    private val selectImageFromGalleryResult = registerForActivityResult(ActivityResultContracts.GetContent()){
        it?.let{ uri ->
            cropImage(uri)
        }
    }
    
    
    
    override fun onCreate(savedInstanceState: Bundle?){
        super.onCreate(savedInstancestate)
        setContentView(R.layout.activity_add_image)
      
        btnSelectImg.setOnClickListener{
            selectImageFromGalleryResult.launch("image/*")
        }
    }
}
```
