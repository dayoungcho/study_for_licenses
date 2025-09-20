# 1. 데이터 모델링의 이해

## 1장. 데이터 모델링의 이해

### 1절. 데이터 모델의 이해

#### 데이터 모델링이란
1) 정보시스템을 구축하기 위한 데이터 관점의 업무 분석 기법
2) 현실 세계의 데이터를 약속된 표기법으로 표현하는 과정
3) 데이터베이스 구축을 위한 분석 및 설계의 과정

- 특징
   - 추상화
   - 단순화
   - 명확성
- 관점
  - 데이터 관점 : 업무가 어떤 데이터와 관련이 있는지 또는 데이터 간의 관계는 무엇인지에 대해서 모델링 하는 방법(What, Data)
  - 프로세스 관점 : 업무가 실제로 하고 있는 일은 무엇인지 또는 무엇을 해야 하는지를 모델링 하는 방법(How, Process)
  - 데이터와 프로세스의 상관 관점 : 업무가 처리하는 일의 방법에 따라 데이터는 어떻게 영향을 받고 있는지 모델링하는 방법(Interaction)

- 유의사항
  - 유일성: 같은 시간에 같은 데이터를 제공
  - 유연성: 사소한 업무변화에 데이터 모델이 수시로 변경되면 안됨(데이터 정의를 사용 프로세스와 분리)
  - 일관성: 데이터 간 상호 연관 관계에 대해 명확하게 정의

- 데이터 모델링의 3단계
  <table style="border: 2px;">
  <tr>
    <th> 개념적 모델링<br>(추상) </th>
    <td> - 추상화 수준이 높음<br>- 업무중심적, 포괄적 수준의 모델링<br>- 전사적 데이터 모델링<br>- EA 수립 시 이용 </td>
  </tr><tr>
     <th>논리적 모델링(정규화)</th>
     <td>- 시스템으로 구축하고자 하는 업무에 대해 <br>    key, 속성 관계 등을 구체적으로 표현<br>- 재사용성 높음</td>
  </tr><tr>
   <th>물리적 모델링(DB)</th>
   <td>- 실제로 데이터베이스에 반영할 수 있도록 <br>물리적 성격을 고려하여 설계 </td>
  </tr>
</table>
 
- 데이터 모델링의 3요소: 엔티티, 관계, 속성 (Things, Relationships, Attributes)
- 모델링의 특징: 추상화, 단순화, 정확화
- 데이터 모델 표기법
  - 1986년 피터 첸이 Entitiy Relationship Model 개발
  - IE, Baker 기법이 많이 쓰임
  - 엔티티 관계 속성으로 이루어짐
- ERD 작업 순서
  1) 엔티티 그림
  2) 엔티티 배치
  3) 엔티티 관계 설정
  4) 관계명 기술
  5) 관계의 참여도 기술
  6) 관계 필수 여부
#### 데이터베이스 스키마 구조
- 외부 스키마: 개개인 사용자가 보는 개인적 DB 스키마
- 개념 스키마: 모든 사용자 관점을 통합한 전체 DB
- 내부 스키마: 물리적 장치에서 데이터가 실제적으로 저장

#### 매핑(사상): 상호 독립적인 개념을 연결시켜주는 다리
- 논리적 사상: 외부 스키마-개념 스키마
- 물리적 사상: 개념 스키마-내부 스키마
 
### 2절. 엔티티
- 정의: 업무에서 관리해야 하는 데이터의 집합, 인스턴스의 집합

- 특징
  1) 업무에서 필요로 함
  2) 유일한 식별자
  3) 2개 이상의 인스턴스 집합
  4) 업무 프로세스에서 이용
  5) 2개 이상의 속성
  6) 관계 가짐
- 분류 기준
  - 유무형에 따른 분류
    <table>
       <tr>
         <th> 유형 엔티티</th>
          <td>물리적 형태가 있음<br>안정적, 지속적으로 활용<br>ex) 사원, 물품 강사</td>
       </tr> <tr>
          <th>개념 엔티티</th>
          <td>물리적 형태 X<br>관리해야 할 개념적 정보로 구분됨<br>ex) 조직, 보험상품 등</td>
       </tr> <tr>
          <th>사건 엔티티</th>
          <td>업무 수행에 따라 발생됨<br>비교적 발생량이 많고 각종 통계자료에 이용 가능<br>ex) 주문, 청구, 미납 등</td>
       </tr>
    </table>

  - 발생 시점에 따른 분류
    <table>
       <tr>
         <th> 기본 엔티티</th>
          <td>업무에 원래 존재하는 정보<br>독립적으로 생성 가능<br>ex) 사원, 부서, 고객, 상품, 자재</td>
       </tr> <tr>
          <th>중심 엔티티</th>
          <td>기본 엔티티로부터 발생<br>그 업무에 있어 중심적인 역할을 함<br>ex) 계약, 사고, 예금원장, 청구, 주문</td>
       </tr> <tr>
          <th>행위 엔티티</th>
          <td>두 개 이상의 부모 엔티티로부터 발생<br>자주 내용이 바뀌거나 데이터량이 증가함<br>ex) 주문목록, 사원변경이력, 프로젝트참여</td>
       </tr>
    </table>

- 엔티티 명명 규칙
  1) 협업에서 사용되는 용어
  2) 약어 지양
  3) 단수 명사
  4) 유일성 보장
  5) 의미 명확
 

### 3절. 속성
- 정의: 업무에서 필요로 하는 인스턴스에서 관리하고자 하는 의미상 더 분리되지 않는 최소의 데이터 단위
- 특징
  1) 업무에서 필요
  2) 주식별자에 함수적으로 종속(기본키가 변경되면 속성도 변경)
  3) 1개의 속성은 1개의 속성값을 가짐
  4) 속성도 집합
 
- 분류 기준
  - 특성에 따른 분류: 기본, 설계, 파생 속성
  - 분해 가능 여부: 단일, 복합, 다중값 속성

- 도메인: 속성이 가질 수 있는 값의 범위

### 4절. 관계
- 관계의 표기 구성
  - 관계명
  - 관계차수: (1:1), (1:M), (N:M)
  - 관계 선택사항: 필수(|), 선택(O)
 
- 분류 기준: ERD
  1) 존재관계: 존재 자체로 연관성이 있는 관계(e.g. 직원-부서, 학생-학과)
  2) 행위관계: 특정 행위를 함으로써 연관성이 생기는 관계(e.g. 회원-주문, 학생-출석부)

### 5절. 식별자
- 정의: 각각의 인스턴스를 구분 가능하게 만들어주는 대표적 속성(자주 이용되는 속성X)
- 특징
  1) 유일성
  2) 최소성
  3) 불변성
  4) 존재성: 속성값이 NULL일 수 없음
 
- 분류
  <table>
  <tr>
    <th>대표성</th>
    <td>주식별자</td>
    <td>보조식별자</td>
  </tr>
  <tr>
    <th>스스로 생성 여부</th>
    <td>내부식별자</td>
    <td>외부식별자</td>
  </tr>
  <tr>
    <th>단일속성 여부</th>
    <td>단일식별자</td>
    <td>복합식별자</td>
  </tr>
  <tr>
    <th>대체 여부</th>
    <td>본질/원조식별자</td>
    <td>인조/대리식별자</td>
  </tr>
</table>


## 2장. 데이터 모델과 SQL
### 1절. 정규화

- 정의: 데이터 정합성을 위해 엔티티를 작은 단위로 분리하는 과정

1. 제 1 정규형
   - 모든 속성이 하나의 값만 가짐
   - 도메인이 원자값만으로 구성
2. 제 2 정규형
   - 엔티티의 모든 일반속성이 모든 주식별자에 종속됨
   - 부분적 함수 종속 제거
3. 제 3 정규형
   - 주식별자가 아닌 모든 속성 간에는 서로 종속 X
   - 속성간 이행적 함수 종속 제거
4. 보이스코드 정규형
   - 후보키가 기본키 속성 중 일부에 함수적 종속일 때 다수의 주식별자 분리

#### 반정규화
- 데이터의 조회 성능 향상을 위해 데이터의 중복을 허용하거나 그룹핑하는 과정
1. 테이블 반정규화
   - 병합
     - 1:1 관계 테이블 병합
     - 1:M 관계 테이블 병험 -> 중복 데이터 생길 수 있음
   - 분할
     - 수직 분할
     - 수평 분할(파티셔닝)
   - 추가
     - 중복 테이블 추가
     - 통계 테이블 추가
     - 이력 테이블 추가
     - 부분 테이블 추가
2. 컬럼 반정규화
   - 중복 컬럼 추가
   - 파생 컬럼 추가
   - 이력 테이블 컬럼 추가
3. 관계 반정규화(중복 관계 추가)
   - JOIN이 필요한 경우가 많을 때 중복 관계를 추가하는 것이 성능 측면에서 유리할 수 있음. <br> => 무결성 깨뜨릴 위험 X
### 2절. 관계와 조인의 이해

- 조인: 식별자를 상속하고, 상속된 속성을 매핑키로 활용하여 데이터를 결합하는 것
- 관계: 식별자를 상속시키고 해당 식별자를 매핑하여 데이터를 결합하는 것
- 식별자 관계(실선)
  - 부모 엔티티의 식별자 = 자식 엔티티의 주식별자
  - 자식 엔티티의 데이터가 반드시 부모 엔티티에 존재해야함
  - 단일식별자면 1:1, 복합식별자면 1:M 관계
- 비식별자 관계(점선)
  - 부모 엔티티의 식별자 = 자식 엔티티의 일반 속성
  - 부모 엔티티 없는 자식 엔티티 생성 가능
  - 자식 엔티티가 존재하는 상태에서 부모 엔티티 삭제 가능
  - 비식별자 관계에서 조인 많이 발생

### 3절. 모델이 표현하는 트랜잭션의 이해

- IE
  - 실선: 필수적 관계
  - 원: 선택적 관계
- 바커
  - 실선: 필수적 관계
  - 점선: 선택적 관계

  
### 4절. Null 속성의 이해

- 특성
  1) 아직 정의되지 않은 값으로 0이나 ""이 아님
  2) NOT NULL, PRIMARY KEY 이외의 모든 데이터 유형에 포함될 수 있음
  3) `NVL`(결측값 처리 함수), `ISNULL`(NULL인지 여부 반환)로 다른 결과값 얻음
  4) 집계 함수에서는 제외됨
- NULL의 연산
  - NULL과의 연산은 NULL을리턴
  - 비교 시 알 수 없음(UNKNOWN) 리턴
  - 집계함수(`SUM` 등)는 NULL을 제외하고 계산

### 5절. 본질식별자 vs. 인조식별자

- 본질식별자(원조식별자): 업무 프로세스에 존재하는

  <table>
  <tr>
    <th>본질식별자(원조식별자)</th>
    <td>- 업무 프로세스에 존재하는 식별자로 가공되지 않은 원래의 식별자</td>
  </tr>
  <tr>
    <th>인조식별자(대리식별자)</th>
    <td>주식별자의 속성이 두 개 이상인 경우 그 속성들을 하나로 묶어서 사용하는 식별자</td>
  </tr>
</table>

1) 인조식별자는 대체로 본질식별자가 복잡한 구성을 가질 때 만들어짐
2) 인조식별자를 사용하면 중복데이터를 막기 어려워짐
3) 인조식별자를 사용하면 본질식별자를 사용할 때와 비교하여 추가적 인덱스가 필요해짐<br>
=> 인조식별자는 단점도 존재하므로 꼭 필요한 경우에만 사용하는 것이 바람직

<br/>

# 2. SQL 기본 및 활용

## 1장. SQL 기본

### 1절. 관계형 데이터베이스 개요

- 데이터베이스: 효율적으로 데이터를 관리하고 손상을 피하며 데이터를 복구하기 위한 시스템(DBMS)

<table style="border: 2px;">
  <tr>
    <th> 명령어 종류 </th>
    <th> 명령어 </th>
    <th> 설명 </th>
  </tr><tr>
     <td>DDL</td>
     <td>CREATE <br> ALTER<br>DROP<br>RENAME</td>
     <td> 데이터 구조 정의</td>
  </tr><tr>
   <td rowspan="2">DML</td>
   <td>SELECT</td>
   <td>조회 및 검색(=RETRIEVE)</td>
  </tr><tr>
     <td>INSERT<br>UPDATE<br>DELETE</td>
     <td>데이터 변형</td>
  </tr><tr>
    <td>DCL</td>
    <td>GRANT<br>REVOKE</td>
    <td>권한 부여 및 회수</td>
  </tr><tr>
    <td>TCL</td>
     <td>COMMIT<br>ROLLBACK</td>
     <td>트랜잭션 제어</td>
  </tr>
</table>

- 일반 집합 연산자
  - `UNION`
  - `INTERSECTION`
  - `DIFFERENCE`
  - `PRODUCT`(`CROSS JOIN`)
 
- 순수 관계 연산자
  - `SELECT`
  - `PROJECT`
  - (NATURAL) `JOIN`
  - DIVIDE(현재 사용 X)
   
- 데이터타입
  - CHARACTER(S)
  - VARCHAR(S)
  - NUMERIC
  - DATETIME


### 2절. SELECT문

```SQL
SELECT [ALL/DISTINCT/(*)] 칼럼명1, 칼럼명2, ...
FROM 테이블명
WHERE 조건
GROUP BY 칼럼
HAVING 조건
ORDER BY 칼럼
```

- 실행순서: `FROM` - `WHERE` - `GROUP BY` - `HAVING` - `SELECT` - `ORDER BY`

<br/>
- ALIAS(별칭)
  - 칼럼명 바로 뒤에 위치
  - 칼럼명과 ALIAS 사이에 `AS` 키워드 사용 가능
  - 이중 인용부호는 ALIAS가 공백, 특수문자를 포함하는 경우나 대소문자 구분이 필요할 때 사용
  - ex) BAND에 B, BAND_MEMBER에 BM이라는 별칭
    ```SQL
    SELECT B.BAND_NAME, BM.MEMBER_NAME
       FROM BAND B, BAND_MEMBER BM
    WHERE B.BAND_CODE = BM.BAND_CODE
    ```
    
- 합성연산자
  - 수직 바 || (Oracle)
  - 플러스 + (SQL Server)
  - CONCAT(string1,string2)
  - ex)
    ```SQL
    SELECT first_name || last_name AS full_name
    FROM employees;
    ```

- `WHERE` 절에는 집계함수 사용 불가

### 3절. 함수

|함수 종류|내용|
|--------|-------|
|문자형 함수|CONCAT, UPPER, LOWER,<br>SUBSTR, LENGTH, TRIM,,<br>REPLACE, INSTR, LEFT,<br>RIGHT, MID등|
|숫자형 함수|ROUND, ABS, POWER,<br>CEIL, FLOOR, MOD, SIGN,<br>SQRT, EXP, LOG 등|
|날짜형 함수|DATEADD, DATEDIFF,<br>YEAR, MONTH, DAY,<br>HOUR, MINUTE, SECOND,<br>DATEPART,GETDATE 등|
|변환형 함수|CAST, CONVERT, TO_CHAR,<br>TO_NUMBER, TO_DATE,<br>NUMTOYMINTERVAL,<br>TO_TIMESTAMP 등|

- `SIGN(숫자)`: 숫자가 양수인지 음수인지 0인지 구별
- `CEIL(숫자)`: 올림
- `FLOOR(숫자)`: 내림
- `TRUNC(숫자,[m])`: 숫자를 m자리에서 반올림, m 생략 시 디폴트=0
- `EXP`: 지수
- `POWER`: 거듭제곱
- `SQRT`: 제곱근
- `LN`: 자연로그

- NULL 관련 함수

|   함수   |   설명   |
|---------|--------|
|NVL(표현식1, 표현식2) | 1이 NULL이면 2 출력 |
|NVL2(표현식1, 표현식2, 표현식 3) | 1이 NULL이면 3, 아니면 2 출력 |
|NULLIF(표현식1, 표현식2 ) | 1=2이면 NULL, 아니면 1 리턴 |
|COALESCE(표현식1, 표현식2, ...) | NULL이 아닌 가장 앞 번째의 표현식 반환 |


### 4절. WHERE 절

|구분|연산자|비고|
|----|-----|-----|
|비교|=, >, >=. <, <=|COLUMN = NULL은 항상 False|
|부정비교|!=, ^=, <>, NOT=|COLUMN <> NULL 은 항상 False|
|논리|AND, OR, NOT||
|SQL|BETWEEN A AND B<br>IN(list)<br>LIKE '비교문자열'<br>IS NULL||
|부정SQL|NOT BETWEEN A AND B<br>NOT IN(list)<br>IS NOT NULL||

- 우선순위

  |순위|연산자|
  |----|------|
  |1|~(비트 NOT)|
  |2|*(곱하기), /(나누기), %(계수)|
  |3|+,-,&(비트 AND), ^(비트 전용 OR), \|(비트OR)|
  |4|비교 연산자|
  |5|NOT|
  |6|AND|
  |7|ALL, ANY, BETWEEN, IN, LIKE, OR, SOME|
  |8|=(할당)|
- 단순 CASE 표현식
  ```SQL
  CASE 표현식
     WHEN 값1 THEN 결과1
     WHEN 값2 THEN 결과2
     ...
     ELSE 결과3
  END
  ```

- 검색 CASE 표현식
  ```SQL
  CASE
     WHEN 조건1 THEN 결과1
     WHEN 조건2 THEN 결과2
     ...
     ELSE 결과3
   END
  ```
- DECODE
  - DECODE(A,B,X,Y): A=B이면 X출력, 아니면 Y출력
  - DECODE(A,B,X,C,Y,Z): A=B이면 X출력, A=C이면 Y출력, 둘 다 아니면 Z출력
- 비교문자열
  - like 'A%' : A로 시작하는 문자열 조회
  - like '_A%' : 두 번째 문자가 A인 문자열 조회
- 참고사항
  - 오라클에 ''를 입력하면 NULL로 입력되어 조회하려면 IS NULL 조건으로 조회해야함. SQL에서는 ''로 저장 및 조회 가능
 

### 5절. GROUP BY, HAVING 절

- 집계함수
  - `COUNT`
    - `COUNT(*)`: 전체 행의 개수
    - `COUNT(칼럼)`: NULL 제외 칼럼 내 행의 개수
    - `COUNT(DISTINCT 칼럼)`: NULL 제외한 행 중 중복을 제거한 이후의 개수
  - `SUM`
  - `AVG`
  - `MAX`/`MIN`
  - `STDDEV`
  - `VARIANCE`/`VAR`

- 특성
   - `SELECT` 절과 달리 ALIAS 사용 불가
   - 일반적으로 `GROUP BY`와 `HAVING`을 같이 사용하지만, 테이블 전체가 하나의 그룹이 되는 경우에는 `HAVING`을 단독으로 사용 가능

### 6절. ORDER BY 절

1) 오름차순(ASC) 디폴트
2) `SELECT`문 내에서 논리적으로 맨 마지막에 수행됨
3) NULL - 오라클에서는 최댓값, SQL에서는 최솟값
4) `SELECT` 절 내에서 1번만 사용 가능(`ORDER BY 칼럼1, 칼럼2` 이런 식으로는 가능)

### 7절. JOIN

#### (1) EQUI JOIN

- (=) 조건으로 join
- ex) PRODUCT와 PRODUCT_REVIEW 테이블에서 PRODUCT_CODE가 '100001'로 일치하는 행의 <br>코드, 이름, 아이디, 리뷰 내용, 그리고 작성일자를 출력
  ```SQL
  SELECT A.PRODUCT_CODE, A.PRODUCT_NAME,
         B.MEMBER_ID, B.CONTENT, B.REG_DATE
  FROM PRODUCT A, PRODUCT_REVIEW B
  WHERE A.PRODUCT_CODE = B.PRODUCT_CODE AND A.PRODUCT_CODE = '100001';
  ```
  
#### (2) NON EQUI JOIN

- (=)이 아닌 다른 조건으로 join
- ex) EVENT와 PRODUCT_REVIEW 테이블에서 리뷰 작성 일자가 이벤트 시작일과 종료일 사이인 행의 <br>이벤트명, 아이디, 리뷰 내용, 리뷰 작성 일자 출력
  ```SQL
  SELECT A.EVENT_NAME, B.MEMBER_ID, B.CONTENT, B.REG_DATE
  FROM EVENT A, PRODUCT_REVIEW B
  WHERE B.REG_DATE BETWEEN A.START_DATE AND A.END_DATE
  ```

  #### (3) INNER JOIN
  
  - 조건을 충족하는 행만 출력
  - `ON`절 사용
  - ex) PRODUCT와 PRODUCT_REVIEW 테이블에서 PRODUCT CODE가 일치하는 행의 <br>코드, 이름, 아이디 리뷰 내용, 작성일자를 출력
    ```SQL
    SELECT A.PRODUCT_CODE, A.PRODUCT_NAME,
         B.MEMBER_ID, B.CONTENT, B.REG_DATE
     FROM PRODUCT A INNER JOIN PRODUCT_REVIEW B
        ON A.PRODUCT_CODE = B.PRODUCT_CODE;
     ```

#### (4) OUTER JOIN

- 조건에 충족하는 데이터가 아니어도 출력될 수 있음
- `ON`절 사용

##### 1) LEFT OUTER JOIN
- 왼쪽 테이블의 데이터는 무조건 출력
- 조건에 맞는 값이 없을 시 오른쪽 테이블 칼럼의 값은 NULL로 출력
- ex) PRODUCT CODE가 일치하는 행에 대해 PRODUCT와 PRODUCT_REVIEW 테이블을 LEFT OUTER JOIN
  ```SQL
  SELECT A.PRODUCT_CODE, A.PRODUCT_NAME,
         B.MEMBER_ID, B.CONTENT, B.REG_DATE
  FROM PRODUCT A LEFT OUTER JOIN PRODUCT_REVIEW B
     ON A.PRODUCT_CODE = B.PRODUCT_CODE;
  ```
  
  |PRODUCT_CODE|PRODUCT_NAME|MEMBER_ID|CONTENT|REG_DATE|
  |:-------------|:-----------|:---------|:-------|:--------|
  |100001|무소음 무선 마우스|sqlbaby01|무소음인데 소음이 조금 있는 듯?|20210320|
  |100001|무소음 무선 마우스|sqlchild02|무선이라 정말 편하네요!|20210324|
  |100002|기계식 게이밍 키보드|sqladult03|게임할 맛 납니다|20210329|
  |100003|무결점 패널 광시야각 모니터|[NULL]|[NULL]|[NULL]|

##### 2) RIGHT OUTER JOIN
- 오른쪽 테이블의 데이터는 무조건 출력
- 나머지는 생략...

##### 3) FULL OUTER JOIN
- 두 테이블의 데이터가 모두 출력됨
- 중복값은 제거됨
```SQL
SELECT A.CAST AS R_CAST, B.CAST AS I_CAST
FROM RUNNING_MAN A FULL OUTER JOIN INFINITE_CHALLENGE B
ON A.CAST = B.CAST
```

|R_CAST|I_CAST|
|:------|:------|
|[NULL]|박명수|
|[NULL]|양세형|
|[NULL]|정준하|
|[NULL]|조세호|
|김종국|[NULL]|
|송지효|[NULL]|
|양세찬|[NULL]|
|유재석|유재석|
|이광수|[NULL]|
|전소민|[NULL]|
|지석진|[NULL]|
|하하|하하|

#### (5) NATURAL JOIN
- A 테이블과 B 테이블에서 같은 이름을 가진 칼럼들이 모두 동일한 데이터를 가질 경우 JOIN
- MSSQL에서는 지원X
  ```SQL
  SELECT * FROM RUNNING_MAN A NATURAL JOIN INFINITE_CHALLENGE B;
  ```
  
  |CAST|GENDER|JOB|
  |:----|:------|:---|
  |유재석|남|개그맨|
  |하하|남|가수|

- `USING` 조건절을 사용하여 동일 여부를 확인할 칼럼을 지정할 수 있음
- 단 `USING` 절로 정의한 칼럼 앞에는 별도의 ALIAS나 테이블명을 붙이면 안됨
  ```SQL
  SELECT CAST, GENDER, A.JOB AS R_JOB, B.JOB AS I_JOB
  FROM RUNNING_MAN A JOIN INFINITE_CHALLENGE B
  USING (CAST, GENDER);
  ```
  
#### (6) CROSS JOIN
- 카티시안 프로덕트
- 조합할 수 있는 모든 경우를 출력
  ```SQL
  SELECT A.NAME, A.JOB,
         B.DRINK_CODE, B.DRINK_NAME
  FROM ENTERTAINER A CROSS JOIN DRINK B;
  ```
  |NAME|JOB|DRINK_CODE|DRINK_NAME|
  |:----|:---|:----------|:----------|
  |김태형|가수, 작곡가|A1001|아메리카노|
  |김태형|가수, 작곡가|B1002|카페라떼|
  |김태형|가수, 작곡가|C1003|콜드브루|
  |김향기|배우|A1001|아메리카노|
  |김향기|배우|B1002|카페라떼|
  |김향기|배우|C1003|콜드브루|

#### (7) HASH JOIN
- 해시 함수를 사용하여 주소 계산, 조인 수행 -> 조인 칼럼의 인덱스가 없어도 조인 가능
- 선행 테이블의 크기가 작아야 함
- 해시 테이블을 메모리에 생성 => CPU 연산량이 많음

#### (8) NESTED LOOP JOIN
- 선행 테이블에서 결합 조건에 일치하는 레코드를 후행 테이블에 반복적으로 탐색하며 조인
1. 선행 테이블에서 조건을 만족하는 첫 번째 행을 찾음
2. 선행 테이블의 조인 키를 가지고 후행 테이블에 조인 키가 존재하는지 찾으로 가서 조인 시도(랜덤 액세스)
3. 후행 테이블의 인덱스에 선행 테이블의 조인 키가 존재하는지 확인
4. 인덱스에서 추출한 레코드 식별자를 이용하여 후행 테이블에 액세스



## 2장. SQL 활용
### 1절. 서브쿼리
#### 스칼라 서브쿼리

- 주로 `SELECT` 절에서 사용
- 한 행, 한 칼럼만을 반환하는 서브쿼리
```SQL
SELECT M.PRODUCT_CODE,
      (SELECT S.PRODUCT_NAME FROM PRODUCT S
         WHERE S.PRODUCT_CODE = M.PRODUCT_CODE) AS PRODUCT_NAME,
       M.MEMBER_ID,
       M.CONTENT
FROM PRODUCT_REVIEW M;
```

#### 인라인 뷰(동적 뷰)
- `FROM`절과 같이 테이블명이 올 수 있는 위치에 사용
- 서브 쿼리를 임시 테이블처럼 사용
```SQL
SELECT M.PRODUCT_CODE, M.MEMBER_ID, M.CONTENT
       S.PRODUCT_NAME, S.PRICE,
FROM PRODUCT_REVIEW M,
     (SELECT PRODUCT_CODE, PRODUCT_NAME, PRICES
        FROM PRODUCT) S
WHERE M.PRODUCT_CODE = S.PRODUCT_CODE
```

#### 중첩 서브쿼리
- `WHERE`, `HAVING` 절에 사용 가능
##### 1) 쿼리와의 관계에 따른 분류
  <table>
  <tr>
    <th>연관 서브쿼리</th>
    <td>메인 쿼리와 관계를 맺고 있음<BR>서브쿼리 내에 메인 쿼리의 칼럼이 존재</td>
  </tr>
  <tr>
    <th>비연관 서브쿼리</th>
    <td>메인 쿼리와 관계를 맺고 있지 않음<BR>서브쿼리 내에 메인 쿼리의 칼럼이 존재하지 않음</td>
  </tr>
</table>

```SQL
SELECT ORDER_NO, DRINK_CODE, ORDER_CNT
FROM CAFE_ORDER A
WHERE ORDER_CNT = (SELECT MAX(ORDER_CNT) FROM CAFE_ORDER B
                   WHERE B.DRINK_CODE = A.DRINK_CODE);
```

##### 2) 반환하는 데이터 형태에 따른 분류
  <table>
  <tr>
    <th>단일 행 서브쿼리</th>
    <td>서브쿼리가 1건 이하의 데이터를 반환<br>단일 행 비교 연산자와 함께 사용<br>(=,>,<= 등)</td>
  </tr>
  <tr>
    <th>다중 행 서브쿼리</th>
    <td>서브쿼리가 여러 건의 데이터를 반환<BR>다중 행 비교 연산자와 함께 사용</td>
  </tr>
<tr>
    <th>다중 칼럼 서브쿼리</th>
    <td>서브쿼리가 여러 칼럼의 데이터를 반환</td>
  </tr>
</table>

- 다중 행 비교 연산자

|연산자|설명|
|------|----|
|IN|결과에 값이 포함되는지 확인(OR조건)|
|ANY, SOME|결과 중 하나라도 조건을 만족하는지 확인|
|ALL|모든 값이 조건을 만족하는지 확인|
|SOME|
|EXISTS|결과가 존재하는지의 여부 확인|
       
 - 다중 칼럼 서브쿼리 예시
```SQL
SELECT * FROM EMPLOYEES
WHERE (JOB_ID, SALARY) IN (SELECT JOB_ID, MAX_SALARY FROM JOBS
                           WHERE MAX_SALARY = 10000);
```

|FIRST_NAME|LAST_NAME|JOB_ID|SALARY|
|:----------|:---------|:------|:------|
|Alexander|Hunold|IT_PROG|10,000|
|Bruce|Ernst|IT_PROG|10,000|


### 2절. 집합 연산자

  <table>
  <tr>
    <th>UNION ALL</th>
    <td>합집합, 중복 행 그대로 출력</td>
  </tr>
  <tr>
    <th>UNION</th>
    <td>합집합, 중복 제거, 자동 정렬</td>
  </tr>  <tr>
    <th>INTERSECT</th>
    <td>교집합, 중복 제거</td>
  </tr>  <tr>
    <th>EXCEPT/MINUS</th>
    <td>앞 쿼리의 결과 집합에서 뒤 커리의 결과 집합을 뺀 차집합. 중복 제거</td>
  </tr>
</table>

- `INTERSECT` 예시
```SQL
SELECT * FROM RUNNING_MAN
INTERSECT
SELECT * FROM INFINITE_CHALLENGE;
```

|CAST|GENDER|JOB|
|:----|:------|:---|
|유재석|남|개그맨|
|하하|남|가수|


### 3절. 그룹함수

#### 집계 함수
- `COUNT`,`SUM`,`AVG`,`MAX`,`MIN` 등

#### 소계 함수

|표현식|출력값|
|------|------|
|ROLLUP(1,2,3)|(1,2,3)으로 그룹핑<br>(1,2)로 그룹핑<br>1로 그룹핑<br>총합계<BR>=> 순서유관|
|CUBE(1,2,3)|(1,2,3)으로 그룹핑<br>(1,2), (1,3), (2,3)으로 그룹핑<br>1, 2, 3으로 그룹핑<br>총합계|
|GROUPING SETS(1,2)|1로 그룹핑<br>2로 그룹핑|

- NULL은 제외하고 집계됨
- 결과값이 없는 행은 출력 X
- 그룹함수 사용 시 소계를 나타내는 행에서 그룹핑의 기준이 되는 칼럼을 제외하고는 모두 NULL값으로 표현됨
  - `GROUPING`: 그룹 함수 사용 시 집계 생성 여부를 반환해줌(기준 컬럼이 집계된 행 0, 그 외 1)
    ```SQL
    SELECT ORDER_DT, GROUPING(ORDER_DT),
           ORDER_ITEM, GROUPING(ORDER_ITEM),
           COUNT(*)
    FROM STARBUCKS_ORDER
    GROUP BY ROLLUP(ORDER_DT, ORDER_ITEM)
    0RDER BY ORDER_DT;
    ```
    |ORDER_DT|GROUPING(ORDER_DT)|ORDER_ITEM|GROUPING(ORDER_ITEM)|COUNT(*)|
    |:-------|-----------------:|:---------|-------------------:|-------:|
    |20210801|0|바닐라 프라푸치노|0|1|
    |20210801|0|아메리카노|0|3|
    |20210801|0|자바칩 프라푸치노|0|1|
    |20210801|0|카페라떼|0|2|
    |20210801|0|쿨라임 피지오|0|1|
    |20210801|0|[NULL]|1|8|
    |...|
    |20210809|0|[NULL]|1|11|
    |20210810|0|모카 프라푸치노|0|1|
    |20210810|0|아메리카노|0|4|
    |20210810|0|자바칩 프라푸치노|0|1|
    |20210810|0|카페라떼|0|1|
    |20210810|0|카페모카|0|1|
    |20210810|0|콜드브루|0|1|
    |20210810|0|한라봉주스|0|1|
    |20210810|0|[NULL]|1|10|
    |[NULL]|1|[NULL]|1|100|

    ```SQL
    SELECT CASE GROUPING(ORDER_DT)
                WHEN 1 THEN 'ALL DATES' ELSE ORDER_DT
           END AS ORDER DT,
           CASE GROUPING(ORDER_ITEM)
                WHEN 1 THEN 'ALL ITEMS' ELSE ORDER_ITEM
           END AS ORDER_ITEM,
           COUNT(*)
    FROM STARBUCKS_ORDER
    GROUP BY ROLLUP(ORDER_DT, ORDER_ITEM)
    ORDER BY ORDER_DT;
    ```

    |ORDER_DT|ORDER_ITEM|COUNT(*)|
    |:-------|:---------|-------:|
    |20210801|ALL_ITEMS|8|
    |20210801|자바칩 프라푸치노|1|
    |20210801|바닐라 프라푸치노|1|
    |20210801|쿨라임 피지오|1|
    |20210801|카페라떼|2|
    |20210801|아메리카노|3|
    |20210802|그린티크림 프라푸치노|1|
    |20210802|한라봉주스|1|
    |...|
    |20210809|한라봉주스|1|
    |20210809|아메리카노|4|
    |20210810|카페라떼|1|
    |20210810|카페모카|1|
    |20210810|콜드브루|1|
    |20210810|ALL ITEMS|10|
    |20210810|자바칩 프라푸치노|1|
    |20210810|모카 프라푸치노|1|
    |20210810|한라봉주스|1|
    |20210810|아메리카노|4|
    
### 4절. 윈도우 함수
- 결과에 대한 처리 함수 -> 결과 건수에 영향 X
- OVER 키워드와 함께 사용됨

#### 1) 순위 함수
- `RANK` : 같은 순위가 존재하면 존재하는 수만큼 다음 순위를 건너뜀
- `DENSE_RANK` : 같은 순위가 존재하더라도 다음 순위를 건너뛰지 않고 이어서 매김
- `ROW_NUMBER` : 동일한 값이라도 각기 다른 순위 부여
  
- ex) 부서별로 급여가 높은 사원부터 순위 매기기
  ```SQL
  SELECT FIRST_NAME, LAST_NAME, DEPARTMENT_ID, SALARY,
         RANK() OVER (PARTITION BY DEPARTMENT_ID ORDER BY SALARY DESC) AS RANK
  FROM EMPLOYEES;
  ```

#### 2) 집계 함수
- `SUM`, `MAX`, `MIN`, `AVG`, `COUNT`
- ex) 과목별 최소 점수를 받은 사람만 출력
    ```SQL
    SELECT STUDENT_NAME, SUBJECT, SCORE
    FROM (SELECT STUDENT_NAME, SUBJECT, SCORE,
                 MIN(SCORE) OVER (PARTITION BY SUBJECT) AS MIN_SCORE
          FROM SQLD)
    WHERE SCORE = MIN_SCORE;
    ```
    - `COUNT`함수는 `WINDOWING`절을 이용하여 범위 설정 가능
 
      |윈도잉절|설명|
      |--------|----|
      |BETWEEN A AND B|프레임 범위 지정|
      |UNBOUNDED<br>PRECEDING/FOLLOWING|프레임 시작<br>끝을 현재 윈도우 그룹의 첫번째/마지막 행으로 설정|
      |N PRECEDING/FOLLOWING|현재 행 기준으로 지정된 수 만큼<br>이전/이후의 행을 나타냄|
      |CURRENT ROW|현재 행 기준으로 윈도우 프레임 설정|

      - ex) 과목별로 본인 점수와 5점 이하로 차이가 나는 건수를 카운트
      ```SQL
      SELECT STUDENT_NAME, SUBJECT, SCORE,
             COUNT(*) OVER (PARTITION BY SUBJECT
                            ORDER BY SCORE DESC
                            RANGE BETWEEN 5 PRECEDING AND 5 FOLLOWING) AS SIMILAR_COUNT
      FROM SQLD;
      ```
 
#### 3) 행 순서 함수
- SQL Server(MSSQL)에서는 지원 X
<BR>
- `FIRST_VALUE`: 파티션 별 가장 선두의 데이터
- `LAST_VALUE`: 파티션 별 가장 끝의 데이터

- ex) FIRST_VALUE 와 LAST_VALUE를 이용하여 과목별 가장 높은 점수를 구하기
  ```SQL
  SELECT STUDENT_NAME, SUBJECT, SCORE,
         FIRST_VALUE(SCORE) OVER (PARTITION BY SUBJECT
                                  ORDER BY SCORE DESC) AS FIRST_VALUE
  FROM SQLD;
  ```
  
  ```SQL
  SELECT STUDENT_NAME, SUBJECT, SCORE,
         LAST_VALUE(SCORE) OVER (PARTITION BY SUBJECT
                                 ORDER BY SCORE
                                 RANGE BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS LAST_VALUE
  FROM SQLD;
  ```
  
- `LAG`: 파티션 별 특정 수 만큼 앞선 데이터
- `LEAD`: 파티션 별 특정 수 만큼 뒤에 있는 데이터
- ex) 과목별로 본인보다 2만큼 앞에 있는(높은) 점수 구하기
  ```SQL
  SELECT STUDENT_NAME, SUBJECT, SCORE,
         LAG(SCORE,2) OVER (PARTITION BY SUBJECT
                            ORDER BY SCORE DESC) AS LAG
  FROM SQLD;
  ```
  
#### 4) 비율 함수
- NTILE 제외, SQL Server(MSSQL)에서 지원 X
<BR>
- `RATIO_TO_REPORT`: 파티션 별 합계에서 차지하는 비율
- `PERCENT_RANK`: 현재 행이 위치하는 백분위 순위 값 ( 맨 위는 0, 맨 끝은 1)
  - ex) 과목별로 나눈 파티션에서 해당 SCORE가 차지하는 백분위 순위 구하기
    ```SQL
    SELECT STUDENT_NAME, SUBJECT, SCORE,
           RANK() OVER (PARTITION BY SUBJECT ORDER BY SCORE) AS RANK,
           COUNT(*) OVER (PARTITION BY SUBJECT) AS COUNT,
           (RANK() OVER (PARTITION BY SUBJECT ORDER BY SCORE)-1) / (COUNT(*) OVER (PARTITION BY SUBJECT)-1) AS "(RANK-1)/(COUNT-1)",
           PERCENT_RANK() OVER (PARTITION BY SUBJECT ORDER BY SCORE) AS PERCENT RANK
    FROM SQLD;
    ```

- `CUME_DIST`: 해당 파티션에서의 누적 백분율
- `NTILE`: 주어진 수 만큼 행들을 n등분 했을 때 현재 행에 해당하는 등급
  - ex)과목별 각 학생 점수의 등급 구하기
   ```SQL
   SELECT STUDENT_NAME, SUBJECT, SCORE,
          NTILE(1) OVER (PARTITION BY SUBJECT ORDER BY SCORE DESC) AS NTILE1,
          NTILE(3) OVER (PARTITION BY SUBJECT ORDER BY SCORE DESC) AS NTILE3,
          NTILE(5) OVER (PARTITION BY SUBJECT ORDER BY SCORE DESC) AS NTILE5
   FROM SQLD;
   ```
   
   |STUDENT_NAME|SUBJECT|SCORE|NTILE1|NTILE3|NTILE5|
   |:-----------|:------|----:|-----:|-----:|-----:|
   |김기탁|데이터모델링의 이해|19|1|1|1|
   |박형준|데이터모델링의 이해|16|1|1|2|
   |이솔|데이터모델링의 이해|15|1|2|3|
   |노정인|데이터모델링의 이해|12|1|2|4|
   |김재덕|데이터모델링의 이해|7|1|3|5|
   |김기탁|SQL기본 및 활용|77|1|1|1|
   |박형준|SQL기본 및 활용|62|1|1|2|
   |이솔|SQL기본 및 활용|50|1|2|3|
   |김재덕|SQL기본 및 활용|42|1|2|4|
   |노정인|SQL기본 및 활용|42|1|3|5|

### 5절. Top-N 쿼리
- `ROWNUM` : WHERE절에서 <이나 <=을 이용해 행 선택
  ```SQL
  SELECT ROWNUM, 이름, 국어, 영어, 수학 FROM EXAM_SCORE
  WHERE ROWNUM<=5;
  ```
- `ROW_NUMBER`, `RANK`, `DENSE_RANK`: 윈도우 함수를 사용해서도 선택 가능
  ```SQL
  SELECT * FROM (SELECT ROW_NUMBER() OVER (ORDER BY 국어 DESC, 영어 DESC, 수학 DESC) AS RNUM, 이름, 국어, 영어, 수학 FROM EXAM_SCORE)
  WHERE RNUM <= 5;
  ```
  
- `TOP` : 상위 N개의 레코드 선택
  - `TOP(n) WITH TIES` : 값이 동일한 경우 함께 출력함
  ```SQL
  SELECT TOP 5 * FROM Customers ORDER BY RegistrationDate DESC;
  ```
- `LIMIT` : 정렬된 결과에서 상위 N개 행 선택
  ```SQL
  SELECT * FROM Products ORDER BY StockQuantity DESC LIMIT 10;
  ```
- `FETCH` : 결과 집합에서 상위 N개 행 선택
  ```SQL
  SELECT * FROM Employees ORDER BY Salary DESC
  FETCH FIRST 3 ROWS ONLY;
  ```

### 6절. 계층형 질의와 셀프 조인
#### 셀프 조인
- 동일 테이블 사이에서 조인을 수행하는 것
- FROM 절에 같은 테이블이 두 번 이상 등장 => ALIAS(별칭) 사용 필수
- ex)<BR> <CATEGORY 테이블>
- 
  |CATEGORY_TYPE|CATEGORY_NAME|PARENT_CATEGORY|
  |-------------|-------------|---------------|
  |대|컴퓨터/디지털/가전|[NULL]|
  |중|컴퓨터|컴퓨터/디지털/가전|
  |중|디지털|컴퓨터/디지털/가전|
  |중|가전|컴퓨터/디지털/가전|
  |소|노트북/PC|컴퓨터|
  |소|모니터/프린터|컴퓨터|
  |소|모바일/태블릿|디지털|
  |소|카메라|디지털|
  |소|영상가전|가전|
  |소|음향가전|가전|

  ```SQL
  SELECT A.CATEGORY_TYPE, A.CATEGORY_NAME
         B.CATEGORY_TYPE, B.CATEGORY_NAME
         C.CATEGORY_TYPE, C.CATEGORY_NAME
  FROM CATEGORY A, CATEGORY B, CATEGORY C
  WHERE A.CATEGORY_NAME = B.PARENT_CATEGORY
    AND B.CATEGORY_NAME = C.PARENT_CATEGORY
  ```
  |CATEGORY_TYPE|CATEGORY_NAME|CATEGORY_TYPE|CATEGORY_NAME|CATEGORY_TYPE|CATEGORY_NAME|
  |-------------|-------------|-------------|-------------|-------------|-------------|
  |대|컴퓨터/디지털/가전|중|컴퓨터|소|노트북/PC|
  |대|컴퓨터/디지털/가전|중|컴퓨터|소|모니터/프린터|
  |대|컴퓨터/디지털/가전|중|컴퓨터|소|모바일/태블릿|
  |대|컴퓨터/디지털/가전|중|디지털|소|카메라|
  |대|컴퓨터/디지털/가전|중|가전|소|영상가전|
  |대|컴퓨터/디지털/가전|중|가전|소|음향가전|
  
#### 계층 쿼리
```SQL
SELECT LEVEL,
       SYS_CONNECT_BY_PATH('['||CATEGORY_TYPE||']'||CATEGORY_NAME, '-') AS PATH
FROM CATEGORY
START WITH PARENT_CATEGORY IS NULL
CONNECY BY PRIOR CATEGORY_NAME = PARENT_CATEGORY;
```

|LEVEL|PATH|
|-----|----|
|1|-[대]컴퓨터/디지털/가전|
|2|-[대]컴퓨터/디지털/가전-[중]가전|
|2|-[대]컴퓨터/디지털/가전-[중]디지털|
|2|-[대]컴퓨터/디지털/가전-[중]컴퓨터|
|3|-[대]컴퓨터/디지털/가전-[중]가전-[소]영상가전|
|3|-[대]컴퓨터/디지털/가전-[중]가전-[소]음향가전|
|3|-[대]컴퓨터/디지털/가전-[중]디지털-[소]모바일/태블릿|
|3|-[대]컴퓨터/디지털/가전-[중]디지털-[소]카메라|
|3|-[대]컴퓨터/디지털/가전-[중]컴퓨터-[소]노트북/PC|
|3|-[대]컴퓨터/디지털/가전-[중]컴퓨터-[소]모니터/프린터|

- `LEVEL` : 현재의 DEPTH 반환 / 루트 노드 1부터 시작
- `SYS_CONNECT_BY_PATH(컬럼, 구분자)`: 루트노드부터 현재 노드까지의 경로 출력
- `START_WITH`: 루트 노드 생성
- `CONNECT BY`: 루트로부터 자식 노드 생성 / 조건에 만족하는 데이터가 없을 때까지 노드를 생성
  - `CONNECT_BY_ROOT 컬럼` : 루트 노드의 주어진 컬럼 값 반환
  - `CONNECT_BY_ISLEAF` : 가장 하위 노드인지의 여부 
- `PRIOR` : 바로 앞에 있는 부모 노드의 값 반환
- `ORDER SIBLINGS BY` : 형제 노드끼리 정렬
- 선지들
  1. SQL Server에서 계층형 질의문은 CTE(Common Table Expression)을 재귀호출함으로써 계층구조를 전개한다.
  2. "" 앵커 멤버를 실행하여 기본 결과 집합을 만들고 이후 재귀 멤버를 지속적으로 실행한다.
  3. 오라클의 계층형 질의문에서 WHERE 절은 모든 전개를 진행한 후 필터 조건으로서 조건을 만족하는 데이터만을 추출하는 데 활용된다.
  4. "" PRIOR 키워드는 CONNECT BY절 뿐만 아니라 SELECT, WHERE 절에서도 사용할 수 있다.
 

### 기타 내용들
- 뷰 사용의 장점
  1. 독립성: 테이블 구조가 변경되어도 뷰를 사용하는 응용프로그램을 변경하지 않아도 된다.
  2. 편리성: 복잡한 질의를 단순하게 작성할 수 있다.
  3. 보안성: 숨기고 싶은 정보를 제외하고 생성할 수 있다.

# 3장. SQL 관리 구문
## 1. DML(Data Manipulation Language)

### (1) INSERT
```SQL
INSERT INTO 테이블명 (컬럼명1, 컬럼명2, ...) VALUES (데이터1, 데이터2, ...);
```
- 테이블에 데이터를 입력
- 명시되지 않은 컬럼에는 NULL값이 입력됨
  - PK나 NOT NULL 제약조건이 걸린 컬럼에는 NULL값 입력 불가
  - 데이터타입이 맞지 않거나 데이터 갯수가 전체 컬럼 갯수와 다를 경우 에러 발생

### (2) UPDATE
```SQL
UPDATE 테이블명 SET 컬럼명=새로운 데이터 (WHERE 수정할 데이터에 대한 조건);
```
- 이미 저장된 데이터를 수정할 때 사용
- WHERE절이 없을 시 테이블 내 모든 데이터가 변경됨

### (3) DELETE
```SQL
DELETE FROM 테이블명 (WHERE 수정할 데이터에 대한 조건);
```
- 이미 저장된 데이터를 삭제할 때 사용
- WHERE절이 없을 시 테이블 내 모든 데이터가 삭제됨
  - 모든 데이터를 삭제하고 싶을 때에는 `TRUNCATE`도 사용 가능(단 TRUNCATE는 ROLLBACK 불가능)

### (4) MERGE
```SQL
MERGE INTO 테이블명 USING 비교 테이블명 ON 조건
WHEN MATCHED THEN
   UPDATE
   SET 컬럼명 = 새로운 데이터[, 컬럼명 = 새로운 데이터, ...]
WHEN NOT MATCHED THEN
   INSERT [(컬럼명1, 컬럼명2, ...)]
   VALUES (데이터1, 데이터2, ...);
```
- 테이블에 새로운 데이터 입력 OR 변경 작업을 한 번에 할 수 있음
- ex) DEPARTMENTS 테이블의 데이터를 DEPARTMENTS_BACKUP 테이블에 반영하기
  ```SQL
  MERGE
     INTO DEPARTMENTS_BACKUP DB
     USING DEPARTMENTS D
     ON (DB.DEPARTMENT_ID = D.DEPARTMENT_NAME)
  WHEN MATCHED THEN
     UPDATE
        SET DB.DEPARTMENT_NAME = D.DEPARTMENT_NAME,
            DB.MANAGER_ID = D.MANAGER_ID,
            DB.LOCATION_ID = D.LOCATION_ID
  WHEN NOT MATCHED THEN
     INSERT (DB.DEPARTMENT_ID, DB.DEPARTMENT_NAME, DB.MANAGER_ID, DB.LOCATION_ID)
     VALUES (D.DEPARTMENT_ID, D.DEPARTMENT_NAME, D.MANAGER_ID, D.LOCATION_ID);
  ```

## TCL(Transaction Control Language)
- 트랜잭션의 특징
  1. 원자성: 연산은 모두 실행되거나 전혀 실행되지 않음
  2. 일관성: 연산 이전 데이터에 문제가 없으면 연산 이후 데이터에도 문제가 없어야함
  3. 고립성: 연산 도중 다른 트랜잭션의 영향을 받지 않음
  4. 지속성: 트랜잭션이 성공적으로 수행되면 변경된 데이터가 영구 저장됨
<br>
- `COMMIT` : INSERT, DELETE, UPDATE 후 변경된 내용을 확정
- `ROLLBACK` : INSERT, DELETE, UPDATE 후 변경된 내용을 취소
- `SAVEPOINT` : ROLLBACK을 수행할 때 전체 작업을 되돌리지 않고 일부만 되돌릴 수 있게 해줌
<br>
- ROLLBACK, COMMIT의 장점
  1. 데이터 무결성 보장
  2. 영구 변경 전 데이터 변경 사항 확인 가능
  3. 논리적으로 연관된 작업을 그룹핑하여 처리 가능


## DDL(Data Definition Language)
- 자동 커밋, 롤백 불가
- 데이터타입
  <table style="border: 2px;">
  <tr>
    <th> 데이터 유형 </th>
    <th> 명령어 </th>
    <th> 설명 </th>
  </tr><tr>
     <td rowspan="3">문자</td>
     <td>CHAR</td>
     <td>크기 고정<br>스페이스는 문자로 안침</td>
  </tr><tr>
     <td>VARCHAR</td>
     <td>크기 가변</td>
  </tr><tr>
     <td>CLOB</td>
     <td>긴 문자열</td>
  </tr><tr>
     <td>숫자</td>
     <td>NUMBER</td>
     <td>설명</td>
  </tr><tr>
     <td>날짜</td>
     <td>DATE</td>
     <td></td>
  </tr>
</table>

### (1) CREATE
```SQL
CREATE TABLE 테이블명 (
   컬럼명1 데이터타입(DEFAULT/NULL 여부),
   컬럼명2 데이터타입(DEFAULT/NULL 여부),
   ...
   CONSTRAINT ...
);
```
- 제약조건

  |제약조건|설명|
  |--------|---|
  |PRIMARY KEY|기본키, 한 테이블에 하나씩만 정의 가능<br>기본키로 지정된 열에는 NULL값 불가<br>자동으로 UNIQUE 인덱스|
  |UNIQUE KEY|고유키, 각각의 행에 대한 고유성 보장<br>기본키와 다르게 NULL값 가능|
  |NOT NULL|NULL값 입력 허용X|
  |CHECK|컬럼에 저장될 수 있는 값의 범위 제한<br>ex) CONSTRAINT CHK_DEL_TN CHECK(DEL_YN IN('Y','N'))|
  |FOREIGN KEY|외래키, 다른 테이블의 컬럼을 참조하고자 할 때 설정해줌<br>참조 무결성 제약 옵션 선택 가능|

- 참조 무결성 제약 옵션

   |제약 옵션|설명|
   |--------|-----|
   |CASCADE|Parent 값 삭제시 Child 값 같이 삭제|
   |SET NULL|Parent 값 삭제시 Child의 해당 컬럼 NULL 처리|
   |SET DEFAULT|Parent 값 삭제시 Child의 해당 컬럼 DEFAULT값으로 변경|
   |RESTRICT|Child 테이블에 해당 데이터가 PK로 존재하지 않는 경우에만 Parent값 삭제 및 수정 가능|
   |NO ACTION|참조 무결성 제약이 걸려있는 경우 삭제 및 수정 불가|
  
   - ex) CONSTRAINT TEACHER_PK PRIMARY KEY (TEACHER_NO)
   - ex) CONSTRAINT TEACHKER_FK FOREIGN KEY (SUBJECT_ID) REFERENCES SUBJECT(SUBJECT_ID)

- 기존에 존재하던 테이블을 복사해서 생성하고 싶은 경우: CREATE 테이블명 AS SELECT * FROM 복사할 테이블명;

### (2) ALTER
- 테이블 구조를 변경할 때 사용
- `ADD COLUMN` : 새 컬럼 추가
```SQL
ALTER TABLE 테이블명 ADD 컬럼명 데이터유형;
```
- `DROP COLUMN` : 기존 컬럼 삭제. 복구 불가
```SQL
ALTER TABLE 테이블명 DROP COLUMN 컬럼명;
```
- `MODIFY COLUMN` : 기존에 있던 컬럼 변경
  - 기존 데이터가 변경하고자 하는 컬럼 데이터 유형보다 크기가 작아야 변경 가능
  - 컬럼에 지정된 데이터가 없는 경우에만 데이터 유형 변경 가능
  - 현재 NULL값이 저장되어 있지 않은 컬럼에만 NOT NULL 제약조건 추가 가능
  ```SQL
  ALTER TABLE 테이블명 MODIFY (컬럼명 데이터유형 [DEFAULT 값] [NOT NULL], 컬렴명2 데이터유형 ...);
  ```
- `RENAME COLUMN` : 기존 컬럼의 이름 변경
  ```SQL
  ALTER TABLE 테이블명  RENAME COLUMN 변경할 컬럼명 TO 변경할 이름;
  ```
- `ADD CONSTRAINT` : 제약조건을 추가하고 싶을 때
  ```SQL
  ALTER TABLE 테이블명 ADD CONSTRAINT 제약조건명 제약조건 (컬럼명);
  ```
- `DROP TABLE` : 테이블 삭제
  - 해당 테이블을 참조하고 있는 다른 테이블이 존재할 경우 CASCADE 옵션을 명시하지 않으면 삭제 X
  - CASCADE CONSTRAINT: 참조 조건도 테이블과 함께 삭제
   ```SQL
   DROP TABLE 테이블명 [CASCADE CONSTRAINT];
   ```
   
- `TRUNCATE TABLE` : 테이블 내 데이터를 모두 제거, 저장 공간 초기화
  ```SQL
  TRUNCATE TABLE 테이블명;
  ```



## DCL(Data Control Language)
- USER를 생성하고 USER에게 데이터를 관리할 권한을 부여하거나 회수
### USER 관련
- `CREATE USER`: 사용자를 생성. CREATE USER권한이 있어야 수해 ㅇ가능
  ```SQL
  CREATE USER 사용자명 IDENTIFIED BY 패스워드;
  ```
- `ALTER USER` : 사용자를 변경
  ```SQL
  ALTER USER 사용자명 IDENTIFIED BY 패스워드;
  ```
- `DROP USER` : 사용자를 삭제
  ```SQL
  DROP USER 사용자명;
  ```

### 권한 관련
- `GRANT` : 사용자에게 권한을 부여
  ```SQL
  GRANT 권한 TO 사용자명;
  ```
- `REVOKE` : 사용자에게 권한을 회수
  ```SQL
  REVOKE 권한 FROM 사용자명;
  ```
### ROLE 관련
- ROLE: 특정 권한들을 하나의 세트처럼 묶은 것.
1. ROLE을 생성 : `CREATE ROLE 롤명`
2. ROLE에 권한 부여 : `GRANT 권한 TO 롤명`
3. ROLE을 사용자에게 부여: `GRANT 롤명 TO 사용자명`'


# 기타사항
- DROP / TRUNCATE / DELETE 비교
  |DROP|TRUNCATE|DELETE|
  |----|--------|------|
  |ROLLBACK 불가|ROLLBACK 불가|COMMIT 이전 <br>ROLLBACK 가능|
  |사용했던 저장공간을 모두 Release|최초 테이블 생성시 할당된 Storage 남기고 Relaease|데이터를 모두  삭제해도 Storage Release되지 않음|
  |테이블 정의 자체를 완전히 삭제|테이블을 최초 생성된 초기 상태로 만듦|데이터만 삭제|
  
