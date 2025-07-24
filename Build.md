# build.gradle.kts 設定関連

## minifyEnabled 
- true,false 설정 
- true시 ProGuard 또는 R8같은 도구를 사용하여 앱 코드에서 사용되지않는 부분 제거
- 앱 설치파일 크기가 줄어들고,실행속도도 향상
- true일시,"코드 난독화"가 적용이됨
- 일반적으로 Debug일시에는 false
---
## 코드 난독화
- 코드의 변수,메서드 이름을 알아보기 어렵게 변경함

## ProGuard 
- 앱의 코드 난독화 및 최적화를 위한 도구 
- 코드 최적화
- 라이브러리 최적화
- minifyEnabled를 true설정후 proguardFiles를 사용하여 규칙파일 생성
- 디컴파일 방지
? 디컴파일이란 컴파일된 실행파일을 사람이 읽을수있는 소스 코드로 되돌리는것
- 앱 관련 코드(R.java 파일,SourceCode,Interface)등.. javac(java compiler)이 컴파일하여 (.class) 파일로 변환하는데 이떄, Proguard 과정이 일어남
```
debug {
    minifyEnabled = true // debug default value = false
    proguardFiles getDefaultProguardFile(
        'proguard-android.txt'
    ),
}
```

## applicationIdSuffix 
> 앱의 고유 식별자인 applicationId 뒤에 붙는 문자열 Play스토어 등록시 사용됨 <br>
> com.example.myapp 

## BuildFeatures 
- Android Interface Definition Language (aidl)
: 거의 안씀
- compose 
: Jetpack Compose 기능 활성화를 위해 사용(composeOptions도 함께 설정 필요)
- buildConfig 
: 기본값 true
- prefab
: C++ 라이브러리의지원여부 
- renderScript 
: RenderScript 기능 활성화 
- resValues
: 리소스값 넣게해줌 ex. resValue("string", "api_key", "123")
- shaders(OpenGL Shading Language)
: 안써도됨, 그래픽 관련앱에서 사용 
- viewBinding 
: ViewBinding기능 활성화할지 안할지? Jetpack Compose안쓰는경우 사용 

---
## composeOptions 
> Jetpack Compose컴파일러와 관련된 설정 지정 




