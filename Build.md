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
- 앱 관련 코드(R.java 파일,SourceCode,Interface)등.. javac(java compiler)이 컴파일하여 (.class) 파일로 변환하는데 이떄, Proguard 과정이 일어남
```
release {

}
```
