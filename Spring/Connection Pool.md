# SPRING

## 4. 커넥션풀(Connection Pool)
- 스프링에서는 커넥션 풀을 직접적으로 제공해주고 있지 않다.   
대신 `c3p0`와 같은 커넥션풀 라이브러리를 이용해서 커넥션풀을 지원하는 DataSource를 설정할 수 있다.    
	
### 4.1. 스프링 커넥션풀 설정 방법
1. pom.xml 파일에 `c3p0` 라이브러리를 추가한다. <a href="Annotation/Annotation.md">[라이브러리 추가 방법]</a>

```xml
<!-- c3p0 라이브러리 -->
<dependency>
    <groupId>com.mchange</groupId>
    <artifactId>c3p0</artifactId>
    <version>0.9.5.2</version>
</dependency>
```

2. 기존 dataSource에 ComboPooledDataSource 객체를 클래스로 설정한다.

```xml
<!-- 1. c3p0 커넥션풀 DataSource 클래스 설정 -->
<bean name="dataSource" class="com.mchange.v2.c3p0.ComboPooledDataSource">
	<property name="driverClass" value="oracle.jdbc.driver.OracleDriver" />
	<property name="jdbcUrl" value="jdbc:oracle:thin:@localhost:1521:XE" />
	<property name="user" value="web" />
	<property name="password" value="1234" />
</bean>
	
<!-- 2. Spring JDBCTemplate 클래스 설정 -->
<bean name="template" class="org.springframework.jdbc.core.JdbcTemplate">
	<property name="dataSource" ref="dataSource" />
</bean>
```

### 4.2. ComboPooledDataSource 클래스의 주요 프로퍼티(속성)
* initialPoolSize : 초기 커넥션풀의 크기. 기본값 3. 
* maxPoolSize : 커넥션풀의 최대 크기. 기본값 15.
* minPoolSize : 커넥션풀의 최소 크기. 기본값 3.		
* 이외에도 많은 속성들이 있다.
		
