# 📘 Kotlin & Android 개발 정리 메모

---

## 🎨 themes.xml 구조 이해

```xml
<style name="AppTheme" ...>   <!-- 앱 전체 스타일 -->
<style name="ActivityTheme" ...> <!-- 특정 액티비티에만 적용 -->
```

✅ 앱 전체 적용은 위쪽 `style`,
✅ 특정 액티비티 적용은 아래쪽 `style`
📌 ※ TopBar 미표시 문제는 `AndroidManifest.xml`에서 해결함

---

## 🏗️ <application> 태그 vs <activity> 태그

```xml
<application>: 앱 전체 설정 정의
<activity>: 개별 화면(Activity)의 속성 정의
```

---

## 🧩 Modifier란?

> Composable을 장식하거나 행동을 추가하는 "수정자"

* UI 꾸밈용 Modifier
* 동작 추가용 Modifier (e.g. 클릭 등)

---

## 🔄 StateFlow / Flow / LiveData

```kt
StateFlow:
- 관찰 가능한 상태 (value 접근 가능)
- 상태 기반, 초기값 필수
- UI 재렌더링 있음 → 일회성 작업에는 부적합

SharedFlow:
- 일회성 이벤트 처리에 적합
- UI 다시 그리지 않음
```

🧠 특정 시점의 데이터 표현 = `State`
📤 State를 전달하는 방식 = `StateFlow`, `SharedFlow`

---

## 🔽 DropDownItem 주요 속성

* `expanded`: 드롭다운 펼침 여부
* `onDismissRequest`: 닫힘 시 콜백

---

## 🛠️ Kotlin 범위 지정 함수

`let`, `with`, `run`, `apply`, `also` → 가독성 향상 목적

---

## 🧷 @Binds vs @Provides

| 항목          | 설명                   |
| ----------- | -------------------- |
| `@Binds`    | 인터페이스 ↔ 구현체 연결만      |
| `@Provides` | 로직 포함 가능 (복잡한 처리 대응) |

---

## 🧩 Entity vs Model

| 용도     | 위치     | 설명                 |
| ------ | ------ | ------------------ |
| Entity | 데이터 계층 | DB 테이블 매핑 객체       |
| Model  | 도메인 계층 | 비즈니스 로직 + UI 상태 표현 |

---

## ⚙️ AGP (Android Gradle Plugin)

* 빌드, 테스트, 배포 과정 자동화 담당 플러그인

---

## 🧱 App Build 개요

```txt
.kt/.java/.xml → Gradle → DEX → AAB/APK
외부 라이브러리 (.JAR, .AAR) → DEX 변환 포함
```

| 포맷     | 설명                                    |
| ------ | ------------------------------------- |
| `.JAR` | 순수 Java 파일                            |
| `.AAR` | AndroidManifest.xml 포함 Android 전용 패키지 |

---

## 🔧 kapt / ksp

| 도구     | 설명                            |
| ------ | ----------------------------- |
| `kapt` | Kotlin → Java → 어노테이션 처리      |
| `ksp`  | Kotlin 전용 경량 어노테이션 처리 도구 (빠름) |

---

## 🧰 빌드 유형 구성

```gradle
defaultConfig:
- 기본 앱 설정 (e.g. minSdkVersion 등)

isMinifyEnabled:
- 코드 난독화/축소 기능
- 앱 크기 줄이고 보안 향상
```

```txt
Minify: 불필요한 공백/주석 제거
Shrink: 사용하지 않는 코드 제거
```

---

## 🌊 Flow 개념

* 생산자 (Repo) → Flow 데이터 입력
* 소비자 (UI) → Flow 데이터 수집

```kt
lifecycleScope.launch {
    flow.collect { ... }
}
```

✅ 구성 변경 대응, 백그라운드에서 낭비 없음

📅 2025/06/19 (Thu)

* SELECT → UI에 자동 반영
* DELETE/UPDATE → UI 변화 없음
* `suspend`와 함께 사용 ❌ (Flow는 자체 비동기)

---

## 🧠 Kotlin 키워드

```kt
out: 제너릭 공변성 → 출력 전용
R: Android 리소스 접근용 자동 생성 클래스
```

---

## ⏱️ LocalDateTime vs Instant

| 항목  | LocalDateTime | Instant  |
| --- | ------------- | -------- |
| 타임존 | ❌ 없음 (로컬 기준)  | ✅ UTC 기준 |
| 용도  | 국내/지역 서비스     | 글로벌 서비스  |

---

## 🔗 onDelete 옵션

1. `CASCADE` : 부모 삭제 시 자식도 삭제됨
2. `RESTRICT` : 자식이 있으면 부모 삭제 차단
3. `SET NULL` : 부모 삭제 시 자식 외래키를 NULL로
4. `NO ACTION` : 아무 동작 없음

---

📦 이 문서는 Kotlin & Android 개발자용 메모 정리용 `.md` 포맷입니다.
✍️ Created by 너
