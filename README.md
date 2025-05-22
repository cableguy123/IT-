# IT
IT情報について忘れないようにメモ帳

# 프레임워크와 라이브러리가 정확히뭐지? 

```
프레임워크는 웹,앱등을 만드는데 사용하는 소프트웨어 개발 환경
예시로는 Django,Spring, Flutter , React Native,SwfitUI,UIKit ..등
라이브러리는 특정 기능을 실행하는 코드의 집합,즉 이미 작성되어있는 코드의 메소드, 모듈 등을 호출해서 사용하는것
예시로는 Axios
```


# SwiftUI와 UIKit의 차이

```
공통점은 iOS의 프레임워크라는것,
차이점은
SwiftUI는 "선언형 프레임워크","단순한 개발과정","복잡한 UI도 적은 양의 코드로 가능" 이라는 것 ,
UIKit는 "명령형 프레임워크","View를 직접 생성하고 제어","더많은 UI제어와 기능을 제공"
```

## 그래서 선언형과 명령형의 차이는? 
```
명령형 프레임워크는 개발자가 프로그램의 흐름을 작성해서 프로그램을 완성해가지만,
선언형 프레임워크는 개발자가 원하는 결과물을 명시적으로 선언하기만 한다면, 프레임워크에게 위임하는것, 이 차이가 제일 크다
```

# MVVM 패턴 
```
Model 
- 앱의 비즈니스 로직과 데이터 처리 담당
- ex API 통신, DB 접근 , 데이터 가공(Date -> String) 등

View
- 사용자에게 보여주는 UI 담당
- ViewModel에게 입력을 전달

ViewModel
- Model이랑 View의 다리 역할
- View에서 받은 사용자 액션을 Model에게 전달
- Model에서 받은 데이터를 UI표현방식으로 가공해서 View에 넘김

장점
- ViewModel의 재사용성이 증가해짐(UI와 데이터 흐름을 분리했기때문에)
- Unit Test 작성이 쉬움
- MVC 소프트웨어 아키텍쳐 처럼 ViewModel이 Controller처럼 책임이 늘어남
- 메모리 누수 방지가 중요해짐

```


# Never 타입 

```
제어권을 호출한 위치로 return 하지 않는다
Never타입은 빈 열거형(enum) 로 선언되어있다
빈 열거형이므로 인스턴스를 생성할수 없다
CPU의 제어권을 돌려주지가 않기때문에
런타임에서 발생할수있는 에러를 미리 발견하고 검증/테스트 하기위해
심각한 에러가 발생하면 앱을 종료시키기 위해 
```

# Combine 
```
비동기 이벤트 처리와 데이터 스트림 관리에 주로 사용
```

# Sink 

```
Publisher로 전달된 데이터를 처리하는데 매우 중요한 역할
Publisher로부터 발행된 값을 수신하고 Subscriber를 생성
클로저를 통해 값을 처리하고 오류 처리도 가능

```
# [Combine]  Subject 

```
> protoco  Subject : AnyObject, Publisher


![image](https://github.com/user-attachments/assets/e1a57ff6-dc08-4b04-9d30-39323eeaabae)

subject를 사용하면 send(_:)를 통해 외부에서도 1,3,5로 이어지는 일련의 스트림에 값을 주입할수있다
Combine이 이때 사용됨

Subject의 종류는 크게 > PassthroughSubject 와 > CurrentValueSubject

```

# [Combine] Cancellable,AnyCancellable
```
cancellation : "Combine"에서 구독관계를 끊는다
cancellable : Cancellation 의 수행기능을 담고있는 프로토콜
AnyCancellable : Cancellable 의 구현부를 작성한 클래스

Cancellable이 ARC로 관리됨,즉 메모리 관련 측면에서 중요한 역할을 함
즉, Combine에서 Publisher 와 Subscriber는 강한 참조 strong 으로 연결되어있기때문에 Cancellable 객체는 메모리에 계속 남아있음


Cancellable은 프로토콜
즉, 그 프로토콜을 따르는 객체는 AnyCancellable 

```


# WebView 
```
API를 통해서 받은 URL을 호출을 해보면 HTML로 웹페이지가 들어오게됨
> 사파리 웹 호출
- 구현하기가 간단함
- https를 받아서 해당 앱을 처리하는게아니라 사파티앱에서 처리하기떄문에 ATS설정을 해줄 필요가없음 

> UIWebView
- WKWebView보다 좀 느림
- 출력은 되지만 뒤로 가기 앞으로 가기 편의 기능들을 직접 구현해야됨
3. WKWebView
4. SFSafariViewController 
```



# XCodeGen 
```
폴더 구조와 프로젝트 스펙에 맞춰서 XCode 프로젝트를 만들어주는 커맨드라인 도구
사용법은 아래에 명시
https://github.com/yonaskolb/XcodeGen/blob/master/Docs/Usage.md
project.xml? 을 주목해야될듯
간단히 얘기하면 프로젝트 껍데기만 기본적으로 만들어주는 내용
xcodeproj파일이 생기는데 .xml으로 이루어져있어서 직접 충돌을 해결할수도있지만, 빠르게 협업할수 있는게 큰 장점
https://motosw3600.tistory.com/73 < 프로젝트 설정 참고
```


# Swift Concurrency (동시성 프로그래밍) 
```
먼저 동시성이란?
-> ContextSwitching을 통하여 스레드의 흐름이 겹치도록 수행하는것을 동시성이라고 정의함
특정 프로세스의 실행 시간이 다른 프로세스의 흐름과 겹치는 상황에서 동시에 실행한다
Swift는 구조화된 방식으로 비동기,병렬 코드작성을 지원함
```

# GCD(Grand Central Dispatch) 
```
동시성 프로그래밍 API(Swfit Concurrency)가 등장하기전 사용되는 동시성 API
Dispatch Queue는 FIFO Queue의 형태로 작업을 순서대로 전달 받음
Dispatch Queue는
1. Serial Queue
2. Concurrent Queue
로 나눠짐
Serial Queue는 추가된 작업을 하나씩 처리
두개 이상의 작업이 동시에 처리되지않기때문에 Queue 기반의 동기화 작업에서 많이 사용됨
Concurrent Queue는 추가된 작업을 동시에 처리함

DispatchQueue.main
즉, mainQueue는 메인 쓰레드에서 동작을함, UI update관련 동작은 mainQueue에서 실행해야함
Serial Queue에 해당함 
```

# 클린 아키텍쳐란 정확히 뭘까? 
```
먼저 아키텍처란?
한마디로 "설계도" 같은 개념, 우리가 만들고자 하는 서비스 혹은 애플리케이션의 구성요소 및 구성요소간의 관계,외부와 구성요소간의 관계등을 정의하고 설명함

특징은 아래와 같다
1. 프레임워크와 독립적이다
2. Testable하다
3. UI와 독립적이다
4. 데이터베이스와 독립적이다
5. 외부 세계와 독립적이다

즉, 테스트하기에 용이하며 확장성이 좋은(응집도가 높고,결합도가 낮은) 아키텍처

각 계층에 대해서 나누자면

Presentation Layer
- 클라이언트로부터 요청을 받아 도메인 계층으로의 전달을 담당

Domain Layer
- 비즈니스 로직에 해당, 오직 로직 수행만에 관심있음

Persistence Layer
- 데이터베이스 관련된 계층이라고 이해하면 될듯?

```
