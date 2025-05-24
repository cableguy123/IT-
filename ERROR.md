

# Sandbox:rsync Error

```
원인은 권한 문제 
앱의 접근을 제한시켜 시스템 리소스와 사용자 데이터를 보호하는 역할 
macOS앱을 배포할려면 이 기능이 활성화되어있어야 AppStore 등록가능

해결 :  Target > BuildSettings > Build Options > User Script Sandboxing 옵션 No로 ( 앱 빌딩시 Yes ) 
```
