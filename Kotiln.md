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
