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
> INNER JOIN은 null값 처리를 못해서 null값 제외함

> OUTER JOIN은 null값 다 들고옴

> 내부 결합 
- INNER JOIN 
- 여러개의 테이블을 결합하여 조건이 일치한것만을 얻음
- INNER 생략 가능, JOIN 안쓰고 WHERE로만으로 가능 

> 외부 결합
- LEFT JOIN,RIGHT JOIN
- 조건이 일치하지않아도 데이터를 취득함
- 즉, 우선할 테이블을 바탕으로 결합하는 이미지 
- LEFT OUTER JOIN은 왼쪽 테이블을 중심으로 조인
- RIGHT OUTER JOIN은 오른쪽 테이블을 중심으로 조인 
- OUTER 생략 가능 
---

> 내부 결합
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
WHERE 절을 주지않아도 같은 컬럼을 자동으로 인식(INNER JOIN 생략가능)
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

> 외부 결합 
- RIGHT OUTER JOIN 
```
SELECT a,b,c,d,e,f,k
FROM A,B
WHERE A.a(+) = B.a; (right조인이면 +부호를 왼쪽에주기!)
```

ANSI JOIN(표준화)
```
SELECT a,b,c,d,e,f,k
FROM A RIGHT OUTER JOIN B 
ON A.a = B.a;
```

- LEFT OUTER JOIN 
```
SELECT a,b,c,e,f,k
FROM A,B 
WHERE A.a = B.a(+) (left조인이면 +부호를 오른쪽에!)
```

ANSI JOIN(표준화)
```
SELECT a,b,c,d,e,f,k
FROM A LEFT OUTER JOIN B
ON A.a = B.a;
```

- FULL OUTER JOIN 
> 제한없이 모든 데이터를 가져올수있다 
```
SELECT a,b,c,d,e,f,k
FROM A FULL OUTER JOIN B 
ON A.a = B.a;
```




