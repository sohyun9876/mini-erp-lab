# SQL 실행 순서
1. FROM   → 테이블 가져오기
2. WHERE  → 필터링
3. SELECT → 컬럼 계산

# LEFT JOIN
- A LEFT JOIN B ON 조건
- A 테이블은 전부 가져오고, B 테이블은 조건이 맞는 것만 붙인다. 맞는 게 없으면 Null

# Self Join
- 같은 테이블을 별칭(alias)으로 두개 인 것처럼 사용
- example
    ```sql
    FROM Employee e
    JOIN Employee m
    ON e.mangerID = m.id
    ```

# GROUP BY + HAVING
- GROUP BY : 같은 값끼리 묶기
- HAVING : 그룹화 후 조건 필터 (COUNT 등 집계함수에 조건 걸 때)
- COUNT() : 그룹 내 행 개수 세기
- WHERE는 그룹화 전 필터, HAVING은 그룹화 후 필터

# MySQL 저장함수 (Stored Function)
- 입력값을 받아서 결과값을 반환하는 재사용 가능한 함수
- 기본 구조
    ```sql
    CREATE FUNCTION 함수이름(파라미터 타입) RETURNS 반환타입
    BEGIN
      RETURN (
          -- 여기에 SQL 쿼리 작성
      );
    END
    ```
- 예시: N번째로 높은 급여 조회
    ```sql
    CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
    BEGIN
      RETURN (
          SELECT DISTINCT salary
          FROM Employee
          ORDER BY salary DESC
          LIMIT 1 OFFSET N-1
      );
    END
    ```
- `CREATE FUNCTION` : 함수 생성
- `(N INT)` : 입력값 (파라미터)
- `RETURNS INT` : 반환 타입 (정수)
- `BEGIN ~ END` : 함수 본문 시작/끝
- `RETURN (...)` : 이 값을 반환

# 그 외 함수들
- DATEDIFF(오늘, 어제) : 날짜 차이를 구하는 함수
- LAG() 윈도우 함수 : 이전 행의 값을 가져오는 함수
    - EX. LAG() OVER () => OVER는 범위(기준) 설정
- FROM 안에 쿼리문(서브쿼리) : 결과를 임시 테이블처럼 만들어서 다시 쓰는 것
- LIMIT + OFFSET
    - LIMIT N : 결과를 N개만 가져오기
    - OFFSET N : 앞에서 N개 건너뛰고 가져오기
    - 조합하면 N번째 값을 정확히 집어올 수 있음
    - DISTINCT와 함께 써야 중복 제거 후 순위가 정확해짐
    - 예시
        ```sql
        SELECT DISTINCT score
        FROM SCORE
        ORDER BY score DESC
        LIMIT 1 OFFSET 2;  -- 2개 건너뛰고 1개 → 3번째로 큰 값
        ```
    - OFFSET 0 → 1번째, OFFSET 1 → 2번째, OFFSET N-1 → N번째