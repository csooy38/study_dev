# JDBC와 DBCP의 차이점

## 1. JDBC(Java DataBase Connectivity)
- 자바와 데이터베이스 간의 연결.
- 데이터베이스에 연결하려면 드라이버(Driver)를 연결하고, 커넥션(Connection)\객체를 받아와야 한다. 
- JDBC 방식을 사용하면 사용자가 요청할 때마다 매번 드라이버를 로딩하고, 데이터베이스에서 커넥션 객체를 생성하여 연결하고 종료하기 때문에 매우 비효율적이고 데이터베이스에 부하가 많이 발생하는 단점이 있다.


## 2. DBCP(DataBase Connection Pool)
- 데이터베이스와 Connection을 맺고 있는 객체를 관리하기 위한 커넥션 풀.
- JDBC의 단점을 극복하기 위해서 사용된다.
- 웹 컨테이너(톰캣 서버)가 실행되면서 커넥션(Connection) 객체를 미리 풀(Pool)에 만들어 놓는다.
- 데이터베이스와 연결된 커넥션(Connection)을 미리 생성해서 풀(Pool) 속에 저장해 두고 있다가 필요할 때마다 가져다가 사용하고 반납한다.
- 미리 생성해 두기 때문에 데이터베이스의 부하를 줄여주고, 유동적으로 연결을 관리할 수 있다.


## 3. JNDI(Java Naming Directory Interface)
- 커넥션 풀에 접근하려면 JNDI 서비스를 이용해야 함. JNDI는 서버에서 관리하고 있는 리소스에 대한 정보를 알고 있는 특정할 리소스를 찾아서 사용할 수 있도록 객체를 반환해 주는 역할을 한다.
- 디렉토리 서비스에 접근하는데 필요한 API이며, 이 API를 이용해서 서버의 자원을 찾을 수 있다.
- 자원이라 함은 데이터베이스 서버 등을 의미하는데 이런 다른 시스템과 연결을 제공하는 객체이다.
- 자원을 서버에 등록할 때에는 고유한 JDNI 이름을 붙여서 사용한다.
- 톰캣 서버에서 이 자원을 관리하는 가상의 디렉토리는 "java:comp/env" 라는 디렉토리. 해당 디렉토리에 고유한 JNDI 이름을 뒤에 붙여서 해당 자원을 찾게 된다. 찾을 때는 lookup() 이라는 메서드를 이용하여 자원을 찾게 되고, 찾은 객체의 타입은 Object 타입이 된다. 따라서 원래의 리소스 타입으로 형변환을 해 주면 된다.
          

----------------------
# 커넥션 풀(Connection Pool) 연결 방법
1) Context 객체를 생성한다.
	- name : 현재 리소스를 등록할 이름을 지정.
	- auth : DBCP를 관리할 관리자 지정(보통 Container or Application)
	- type : 리소스의 타입을 지정. 커넥션 풀을 사용할 수 있도록 하는 객체의 반환 타입을 의미.
	- url : 접속할 DB 서버의 url을 지정.
	- driverClassName : DB 작업을 로딩할 드라이버. JDBC 방식에서 Class.forName()의 인자값을 의미.
	- username : DB 서버에 로그인할 계정을 지정.
	- password : DB 서버에 로그인할 계정의 비밀번호를 지정.
	- maxActive : 생성할 Connection의 개수를 지정. 동시에 최대로 데이터베이스에 연결할 수 있는 Connection 수를 의미.
	- maxIdle : 커넥션 풀에 여분으로 남겨질 최대 Connection 개수를 지정.    

```xml
<!-- Server 폴더의 Context.xml Source 하단에 작성 -->

<Resource 
	name="jdbc/myoracle"
	auth="Container"
	type="javax.sql.DataSource"
	url="jdbc:oracle:thin:@localhost:1521:XE"
	driverClassName="oracle.jdbc.driver.OracleDriver"
	username="web"
	password="1234"
	maxActive="200"
	maxIdle="100"
/>
```

2) lookup() 메서드를 이용하여 매칭되는 커넥션을 찾는다.
3) DataSource.getConnection() 메서드를 이용하여 커넥션을 확보한다.


# 커넥션 풀을 사용하기 위해서 필요한 라이브러리
- commons-connection-3.2.1.jar
- commons-dbcp-1.4.jar
- commons-pool-1.6.jar
      
          







