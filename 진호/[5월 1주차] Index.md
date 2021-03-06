# 데이터베이스 인덱스

데이터베이스에서의 검색속도 향상을 위한 별도의 자료구조

# 인덱스 고려사항

1. where절에 자주 사용 되는 속성이여야 한다.
2. 조인에 자주 사용되는 속성이여야 한다.
3. 데이터의 중복도가 낮은 속성이여야 한다.

WHY? 무조건 좋은거 아니야?

- 인덱스는 Insert,Update,Delete에서 효율을 희생 (인덱스를 구성해야하기에)
- 별도의 저장공간이 필요하다 ( DB의 보통 10퍼 )

# 인덱스 자료구조

1. 해시 테이블

   ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7e205e98-25ec-41e2-ab41-f0704276818b/Untitled.png)

   - key-value의 구조로 데이터를 저장
   - 빠른 데이터 검색이 필요할때 유용
   - 사용빈도는 낮음 ㅠ (등호 연산에만 특화되어 있어서)

2. B-Tree ( Balanced Tree )

   ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2b9b0952-f4a8-4ae0-8726-044fb5a578b7/Untitled.png)

   ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/78ebba87-e023-483f-97f5-67fd60649d2c/Untitled.png)

   - branch노드에 key-data값을 가지며 Root→Branch→Leaf 순으로 탐색
   -

3. B+Tree
   - 잘 아시는분 팁점... 이해가 안되네요

# Clusterd / Non-Clustered Index

![스크린샷 2022-05-01 오후 10.03.07.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/39f099c8-caec-440a-950d-7a3f654276c5/스크린샷_2022-05-01_오후_10.03.07.png)

- Clusted Index
  - 테이블 당 1개만 존재
  - PK 제약조건으로 컬럼을 생성하면 자동으로 생성
  - 인덱스에 데이터 페이지가 함께 존재
  - 리프 페이지 == 데이터 페이지
  - 데이터가 정렬된 상태

![스크린샷 2022-05-01 오후 10.08.32.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b81ab94c-ce00-4c92-b3a9-7cfdf0625b54/스크린샷_2022-05-01_오후_10.08.32.png)

- Non-Clustered Index
  - Secondary Index ( 보조 인덱스 )
  - 테이블에 여러개 존재할 수 있음
  - Unique 제약조건으로 컬럼을 생성하면 자동으로 생성
  - 인덱스와 데이터 페이지가 따로 존재
  - 리프 페이지에서 데이터가 있는 곳의 주소를 가짐
  - 데이터 페이지에 데이터가 정렬되지 않아도 댐
  - Clustered와 비교하여 조회 속도가 약간 느림
  - Clustered와 비교하여 Insert / Update / Delete 시 부하가 적음

# Cardinality

중복도가 낮으면 카디널리티가 높다. ( 중복도와 상반된 관계 )

참고 :

[https://www.youtube.com/watch?v=P5SZaTQnVCA](https://www.youtube.com/watch?v=P5SZaTQnVCA)

[https://velog.io/@zerodin/데이터베이스-인덱스](https://velog.io/@zerodin/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%9D%B8%EB%8D%B1%EC%8A%A4)

[https://velog.io/@emplam27/자료구조-그림으로-알아보는-B-Tree](https://velog.io/@emplam27/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EA%B7%B8%EB%A6%BC%EC%9C%BC%EB%A1%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EB%8A%94-B-Tree)
