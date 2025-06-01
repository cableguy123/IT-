# themes.xml
```
윗 부분 <style> 태그랑 밑 부분 <style>는 뭔 차이?
간단히 말하면 윗 부분 <style> 태그는 앱 전체에만
밑 부분 <style>는 특정 액티비티에서만 적용됨

-> 해결함, 상단에 컴포넌트 TopBar가 표시가 프리뷰에서는 확인이되었었는데 이상하게 실제 디버깅시에는 표시가 안되어있었음
AndroidManifest.xml에서 해결함

```

# <application> 태그와 <activity> 태그 차이는 뭐야? 
```
<application> 태그안에 있는것들은 앱 전체의 설정을 정의함
<activity> 태그는 각 앱 내의 존재하는 각각의 화면을 정의함
```

# Modifier 이란 무엇인가?
```
의미는 수정자, 이걸 쓰면 Composable을 장식,강화할수도 있다 
1. UI 구성요소들을 꾸미기 위한 Modifier
2. 행동을 추가하기 위한 Modifier 
```

# StateFlow,Flow,LiveData
```
StateFlow
- 현재 상태와 새로운 상태 업데이트를 수집기에 내보내는 관찰 가능한 상태
- value 속성을 통해서도 현재 상태 값을 읽을수있음
- 상태를 업데이트하고 흐름에 전송하려면 MutableStateFlow 클래스의 value속성에 새값을 할당
- 즉, 관찰 가능한 변경 가능상태를 유지해야 하는 클래스에 아주 적합
- State를 가지고 있는 상태를 표현하기때문에 초기값이 필요하고 하나의 값만 업데이트

즉 , 이해하자면
특정 시점에서 어떤 데이터 값을 가지고있는지 나타내는것이 State
그 State를 어떻게 보내는지에 대해 따라 다른 API는 StateFlow,SharedFlow

즉 정리하자면 일회성 작업은 StateFlow에게 적합하지않음 ? 왜 UI를 다시 그리기 때문에
SharedFlow는 일회성 작업에 적합함 UI를 다시 그리지않기때문에 
```

# DropDownItem 
```
Expanded:  DropDownMenu가 펼쳐졌는지 여부
onDismissRequest: DropDownMenu를 닫으라는 명령이 떨어졌을때 동작 
```

# let,with,run,apply..
```
이것들을 모아서, 범위 지정 함수라고함
그냥 단순히 보기 쉽게하기위해서임 
```

# @Binds,@Provides차이
```
@Binds는 구현체(Impl)와 인터페이스를 연결할때 단순화 작업을 함
@Provides는 구현체와 인터페이스를 연결할뿐만 아니라 복집한 로직까지 있을경우에 사용
```

# Entity,Model 차이 
```
Entity는 데이터레이어에서 사용하는 실제 DB의 테이블명명을 가르킴
Model는 도메인레이어에서 사용하는 비즈니스 로직과 UI 처리 담당을 가르킴 즉, Model은? 비즈니스 로직은 도메인 레이어
```

# AGP(Android Gradle PlugIn) 
```
안드로이드 앱의 빌드 및 배포 과정을 관리하는데 사용되는 다양한 플러그인
```

# App Build
```
Gradle을 통해 자동으로 앱을 빌드시켜줌
- .kts
- .java
- .xml
등의 파일들을 컴파일,assemble하여 하나의 AAB(Android App Bundle)로 만들어 배포하고 다운로드 하는 사용자들은
AAB중 .APK 형식으로 다운로드하여 사용
즉, 작성한 코드를 DEX파일로 전환 한 뒤, APK로 묶어줌
이떄! 외부 라이브러리 build.gradle.kts (:app)..은 JAR,AAR형식으로 외부에서 다운로드 받아오고
해당 형식의 파일을 컴파일러가 DEX파일로 변경시킨다

** JAR(Java Archive : 순수 Java 파일)
** AAR(Android Archive: AndroidManifest.xml등 포함) 
```

# kapt/kap 
```
Kapt(Kotiln Annotation Processing Tool)
- Kotiln 코드에서 Java의 어노테이션 프로세서를 사용할수 있도록 해주는 도구
- Kotiln -> Java -> 그 결과를 어노테이션 프로세서를 통해 실행
KSP(Kotiln Symbol Processing)
- Kotiln용으로 설계된 경량의 어노테이션 프로세싱 도구
- Kotiln 코드에서 직접 어노테이션을 처리하여 추가적인 변환 단계없이 더 빠르게 동작 
```


