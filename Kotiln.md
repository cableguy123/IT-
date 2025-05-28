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
