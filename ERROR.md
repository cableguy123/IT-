# 📘 Kotiln Error メモまとめ

## Sandbox:rsync Error

```
원인은 권한 문제 
앱의 접근을 제한시켜 시스템 리소스와 사용자 데이터를 보호하는 역할 
macOS앱을 배포할려면 이 기능이 활성화되어있어야 AppStore 등록가능

해결 :  Target > BuildSettings > Build Options > User Script Sandboxing 옵션 No로 ( 앱 빌딩시 Yes ) 
```
---

## There are multiple indices with name d. This happen if you've declared the same index multiple times or different indices have the same name. See @Index documentation for details.

원인 : 인덱스 이름이 중복됬음

<h2>단일 컬럼 인덱스</h2>

> 하나의 컬럼으로 구성된 인덱스


```
@ColumnInfo(index = true)
``` 
- 단일 컬럼에 대한 간단한 인덱스 
- Room이 자동으로 이름을 지음


<h2>명시적 인덱스 관리용</h2>

> 데이터베이스에서 인덱스를 직접 생성하고 관리하는것을 의미

```
@Entity(indicies = [])
```
- 단일,복합 인덱스로 모두가능
- 이름 직접 설정가능
- 처음부터 복합도 고려가능 

---

## Schema export directory was not provided to the annotation processor so Room cannot export the schema. You can either provide `room.schemaLocation` annotation processor argument by applying the Room Gradle plugin (id 'androidx.room') 

<h2>Room 라이브러리 데이터베이스 스키마 생성시, 경고</h2>

> exportSchema 옵션에 의한 경고문구 

> DB구조정보를 JSON파일 형태로 폴더에 내보냄 

- exportSchema는 Boolean타입
- 데이터베이스 스키마를 폴더로 내보낼지 정할수있음
- default 값은 true 
- 폴더 경로를 정해주지않아서 위의 경고가 발생했음 
- build.gradle(App)에서 defaultConfig 하위 섹션에서 스키마 경로 작성

```
android {
    ...
    
    defaultConfig {
        javaCompileOptions {
            annotationProcessorOptions {
                arguments += ["room.schemaLocation": "$projectDir/schemas".toString()]
            }
        }
    }
}
```
---
