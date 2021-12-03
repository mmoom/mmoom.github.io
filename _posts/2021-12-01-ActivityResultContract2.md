---
layout: single
title:  "[Android, Kotlin] ActivityResultContract API (2) 갤러리에서 사진 가져오기"
---


```
class AddImageActivity : AppCompatActivity(){

    //콜백 선언 - 이미지선택
    private val selectImageFromGalleryResult = registerForActivityResult(ActivityResultContracts.GetContent()){
        it?.let{ uri ->
            //선택된 이미지 결과값(이미지 uri)으로 이미지 크롭하기
            cropImage(uri)
        }
    }
    
    //콜백 선언 - 이미지크롭
    private val cropActivityResultContract = object: ActivityResultContract<Uri?, Uri?>(){
        override fun createIntent(context: Context, input: Uri?): Intent {
            return CropImage.activity(input)
                            .setAspectRatio(1,1)
                            .getIntent(this@AddImageActivity)
        }
        
        override fun parseResult(resultCode: Int, intent: Intent?): Uri? {
            return CropImage.getActivityResult(intent)?.uri
        }
    }
    private lateinit var cropActivityResultLauncher : ActivityResultLauncher<Uri?>
    
    override fun onCreate(savedInstanceState: Bundle?){
        super.onCreate(savedInstancestate)
        setContentView(R.layout.activity_add_image)
      
        btnSelectImg.setOnClickListener{
            //launch를 사용하여 선언한 콜백을 실행
            selectImageFromGalleryResult.launch("image/*")
        }
        
        //크롭된 이미지 결과값
        cropActivityResultLauncher = registerForActivityResult(cropActivityResultContract){ uri ->
            //최종 크롭된 이미지 imageView에 보여주기
            imageView.setImageURI(uri)
        }
    }
    
    //이미지 크롭하는 콜백을 실행
    fun cropImage(uri: Uri){
        cropActivityResultLauncher.launch(uri)
    }
}
```
