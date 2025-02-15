# DML

> 만들어진 테이블의 자료들을 CURD

## 1. INSERT

```sql
INSERT INTO 테이블명 (COLUMN_LIST)VALUES (COLUMN_LIST에 넣을 VALUE_LIST);
INSERT INTO 테이블명VALUES (전체 COLUMN에 넣을 VALUE_LIST);
```

> value 로 '' 이나 NULL 이라고 써주면 정의되지 않은 미지의 값이 됨

## 2. UPDATE

> ```sql
> UPDATE 테이블명 SET 수정되어야 할 칼럼명 = 수정되기를 원하는 새로운 값;
> ```
>
> Ex) 선수 테이블의 백넘버를 일괄적으로 99로 수정한다.
>
> UPDATE PLAYER SET BACK_NO = 99; 480개의 행이 수정되었다.
>
> ex) 선수 테이블의 포지션을 일괄적으로 ‘MF’로 수정한다.
>
> UPDATE PLAYER SET POSITION = 'MF'; 480개의 행이 수정되었다.

## 3. DELETE

> ```sql
> DELETE [FROM] 삭제를 원하는 정보가 들어있는 테이블명;
> ```
>
> 이때 FROM 문구는 생략이 가능한 키워드 이며, 뒤에서 배울 WHERE 절을 사용하지 않는다면 테이블의 전체 데이터가 삭제된다.

## 4. SELECT

> ```
> 조회하기를 원하는 칼럼명을 SELECT 다음에 콤마 구분자(,)로 구분하여 나열하고, FROM 다음에 해당 칼럼이 존재 하는 테이블명을 입력하여 실행시킨다. 입력한 선수들의 데이터를 조회한다.
> ```
>
> DISTINCT 옵션
>
> ​	중복을 제거해줌
>
> WILDCARD 옵션
>
> ​	보고싶은 칼럼 조회해서 봄
>
> ALIAS 부여하기
>
> ​	조회된 결과에 일종의 별명 (ALIAS, ALIASES) 를 부여해 칼럼 레이블을 변경할 수 있음
>
> ```sql
> [예제] SELECT PLAYER_NAME AS 선수명, POSITION AS 위치, HEIGHT AS 키, WEIGHT AS 몸무게 FROM PLAYER; 칼럼 별명 에서 AS를 꼭 사용하지 않아도 되므로, 아래 SQL은 위 SQL과 같은 결과를 출력한다. SELECT PLAYER_NAME 선수명, POSITION 위치, HEIGHT 키, WEIGHT 몸무게 FROM PLAYER;
> 
> [실행 결과] 선수명 위치 키 몸무게 ----- --- -- ---- 정경량 MF 173 65 정은익 MF 176 63 레오마르 MF 183 77 명재용 MF 173 63 변재 섭 MF 170 63 보띠 MF 174 68 비에라 MF 176 73 서동원 MF 184 78 안대현 MF 179 72 양현정 MF 176 72 유원섭 MF 180 77 김수 철 MF 171 68 임다한 DF 181 67 :::: 480개의 행이 선택되었다.
> ```

## 산술 연산자와 합성 연산자

- 산술 연산자

  > 산술 연산자는 NUMBER와 DATE 자료형에 대해 적용되며 일반적으로 수학에서의 4칙 연산과 동일하다. 그리고 우선순위 를 위한 괄호 적용이 가능하다. 일반적으로 산술 연산을 사용하거나 특정 함수를 적용하게 되면 칼럼의 LABEL이 길어지게 되고, 기존의 칼럼에 대해 새로운 의미를 부여한 것이므로 적절한 ALIAS를 새롭게 부여하는 것이 좋다. 그리고 산술 연산자 는 수학에서와 같이 (), *, /, +, - 의 우선순위를 가진다.'
  >
  > ```sql
  > [예제] 선수들의 키에서 몸무게를 뺀 값을 알아본다.
  > [예제] SELECT PLAYER_NAME 이름, HEIGHT - WEIGHT "키-몸무게" FROM PLAYER;
  > [실행 결과] 이름 키-몸무게 --- ------- 정경량 108.00 정은익 113.00 레오마르 106.00 명재용 110.00 변재섭 107.00 보띠 106.00 비에 라 103.00 서동원 106.00 안대현 107.00 양현정 104.00 유원섭 103.00 김수철 103.00 임다한 114.00 ... ... 480개의 행이 선택되었 다.
  > ```

- 합성 (CONCATENATION) 연산자

  > \- 문자와 문자를 연결하는 경우 2개의 수직 바(||)에 의해 이루어진다. (Oracle) - 문자와 문자를 연결하는 경우 + 표시에 의해 이루어진다. (SQL Server) - 두 벤더 모두 공통적으로 CONCAT (string1, string2) 함수를 사용할 수 있다. - 칼럼과 문자 또는 다른 칼럼과 연결시킨다. - 문자 표현식의 결과에 의해 새로운 칼럼을 생성한다. 