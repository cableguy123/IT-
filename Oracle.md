# Oracle 


## 실제 오라클 구조 

           [ CDB (XE) ]  ← 전체 Oracle DB 인스턴스
           ┌────────────────────────────────┐
           │                                │
           │   ┌────────────────────┐       │
           │   │  PDB (XEPDB1)      │       │   ← 하나의 작은 "논리적 데이터베이스"
           │   │  ┌──────────────┐ │       │
           │   │  │  USER: SYSTEM│ │       │   ← 관리자 계정
           │   │  │  USER: PINGT │ │       │   ← 너가 만든 사용자
           │   │  │  USER: userA │ │       │
           │   │  └──────────────┘ │       │
           │   └────────────────────┘       │
           │                                │
           └────────────────────────────────┘

## Oracle 12c 

- Multi-tenant 기능 도입 
- 하나의 DB에 여러개의 DB가 포함 

## CDB

> Container DB 

- 컨테이너 역할을 하는 DB 
- PDB에 필요한 메타정보 저장 
- 서버 그 자체
## PDB

> Pluggable DB 

- 넣었다 뺐다 할수있는 DB 
- CREATE DATABASE mydb; 로 만든 DB하나 

## Oracle 세션이란? 

- DB 접속하게되면 세션이 생성됨
- SID(Session Identifier)와 SERIAL# (serial number)을 가짐 
- myslq -u root -p로 연결된 상태
- 즉,로그인한 하나의 연결상태 라고 보면됨 


## XEPDB1란? 



