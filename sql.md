# Oracle SQL Siver (문제 해설)

## 

## SYNONYM 

- プライベートシノニム作成する


```
・IDはサイズ2の数値型で、NULL値を入力できない
IDには重複した値を入力できない
```
- ID는 사이즈2의 숫자형, NOT NULL 
- 중복 X 
- ID NUMBER(2) UNIQUE NOT NULL 
- ID NUMBER(2) PRIMARY KEY 도 됨! 


# INTERSECT연산자

# SEQUENCE 

# NEXTVAL 

# CURRVAL 


# 단일행함수


# 오브젝트권한 


# FOR UPDATE NOWAIT


# INVISIBLE


# JOIN 정리 

1. INNER JOIN 
- EQUI JOIN 
A,B테이블 둘다 똑같은 컬럼을 가지고있고 
서로 교집합 되는 부분을 조인시켜 
A,B테이블의 나머지 컬럼을 가지고올수있다.
A 테이블의 컬럼이 10,20,30이고 
B 테이블의 컬럼이 10,20,30,40이라면 
교집합되는 10,20,30의 데이터만 가져올수있으며,B테이블 40인 데이터는 가져올수없다 

```
SELECT a,b,c,d,e,f
FROM A INNER JOIN B 
ON A.a = B.a;
```
- NATURAL JOIN 
EQUI 조인과 같으며
WHERE 절을 주지않아도 같은 컬럼을 자동으로 인식
```
SELECT a,b,c,d,e,f
FROM A INNER JOIN B 
```

- JOIN ~ USING
EQUI 조인과 같으며 사용법만 다름
```
SELECT a,b,c,e,f,k 
FROM A JOIN B USING (a)
```
2. OUTER JOIN 
```

```
- LEFT OUTER JOIN 
- RIGHT OUTER JOIN 
- FULL OUTER JOIN 



