### PreparedStatement

** 데이터베이스 관리 시스템(DBMS)에서 동일하거나 비슷한 데이터베이스 문을 높은 효율성으로 반복적으로 실행하기 위해 사용되는 기능**

1. 준비(Prepare) : 먼저 애플리케이션은 SQL문의 틀을 만들고 이를 DBMS로 보낸다.

1. SQL문의 틀을 컴파일하여 그 결과만 저장한다.
2. 실행(Execute) : 변수의 값을 바인드하면 SQL문을 실행한다.

Statement는 매번 쿼리를 수행할때 마다 컴파일을 거치게되고

PreparedStatement는 처음 한 번만 세단계를 거친후 캐시에 담아 재사용을 한다.

Statement

``` jsx
String sql="SELECT name,age FROM TABLE WHERE userId = " +userID;
Statement stmt = conn.createStatement();
ResultSet rs = stmt.executeQuery(sql);
```

PreparedStatement

```jsx
String sql="SELECT name,age FROM TABLE WHERE userId = ?";
PreparedStatement pstmt = conn.prepareStatement();
pstmt.setInt(1,userID);
ResultSet rs = stmt.executeQuery(sql);
```
