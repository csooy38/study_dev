# MyBatis

## 1. MyBatis
- 객체지향언어인 자바의 관계형 데이터베이스 프로그래밍을 좀 더 쉽게 구현할 수 있도록 도와주는 개발 프레임워크.
- 자바는 JDBC API를 제공하지만, 이런 JDBC를 이용하면 한 개의 클래스에 반복된 코드가 존재, 한 파일에 Java 언어와 SQL 언어가 섞여 있어서 재사용성 등이 안 좋아지는 단점이 발생한다.
- MyBatis는 이러한 JDBC의 단점들을 개선했으며, 개발자가 작성한 SQL 명령어와 자바 객체를 매핑해주는 기능을 제공하며, 기존에 사용하던 SQL 명령어를 재사용 가능하게 한다.

### 1.1. MyBatis의 특징
- 한 두 줄의 자바 코드로 DB 연동을 처리.
- SQL 명령어를 자바 코드에서 분리하여 XML 파일에 따로 관리.

### 1.2. MyBatis 설정 작업
- 스프링과 MyBatis를 연동하기 위한 라이브러리 설정 - pom.xml
	- MyBatis 프레임워크 라이브러리 추가.
	- MyBatis-Spring 라이브러리 추가
	- Spring-JDBC 라이브러리 추가.
	- 데이터베이스와 연결을 담당하는 DataSource 객체 설정. 
	
```xml
<!-- mybatis 프레임워크 라이브러리 -->
<dependency>
    <groupId>org.mybatis</groupId>
    <artifactId>mybatis</artifactId>
    <version>3.4.6</version>
</dependency>
```

```xml
<!-- mybatis-spring 라이브러리 -->
<dependency>
    <groupId>org.mybatis</groupId>
    <artifactId>mybatis-spring</artifactId>
    <version>1.3.2</version>
</dependency>
```

```xml
<!-- spring-jdbc 라이브러리 -->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-jdbc</artifactId>
    <version>${org.springframework-version}</version>
</dependency>
```

#### [예]

* **root-context.xml**
myBatis 설정.

```xml
<!-- 스프링 작업시 설정 파일을 설정하는 공간 -->
	
<!-- 1. c3p0 커넥션풀 DataSource 클래스 설정 -->
<bean name="dataSource" class="com.mchange.v2.c3p0.ComboPooledDataSource">
	<property name="driverClass" value="oracle.jdbc.driver.OracleDriver" />
	<property name="jdbcUrl" value="jdbc:oracle:thin:@localhost:1521:XE" />
	<property name="user" value="web" />
	<property name="password" value="1234" />
</bean>
	
<!-- 2. SqlSessionFactory 클래스 설정 -->
<bean name="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
	<property name="dataSource" ref="dataSource" />
	<property name="mapperLocations" value="classpath:/mapper/*.xml/" />
</bean>
	
<!-- 3. SqlSessionTemplate 클래스 설정 -->
<bean name="sqlSession" class="org.mybatis.spring.SqlSessionTemplate">
	<constructor-arg ref="sqlSessionFactory" />
</bean>
```

* **servlet-context.xml**
com.spring 패키지 아래에 있는 모든 파일들을 자동으로 읽도록 설정.

```xml
<context:component-scan base-package="com.spring" />
```

* **EmpDAO 인터페이스**

```java
public interface EmpDAO {
	public List<EmpDTO> getEmpList();
}
```

* **EmpDAOImpl 클래스**
EmpDAO 인터페이스를 상속받아 추상메서드를 오버라이딩 한다.   
`this.sqlSession.selectList(" id ")`로 emp.xml에서 동일한 `id`의 sql문을 실행 후 값을 받아온다.  

```java
@Repository
public class EmpDAOImpl implements EmpDAO {

	@Autowired
	private SqlSessionTemplate sqlSession;
	
	@Override
	public List<EmpDTO> getEmpList() {
		
		return this.sqlSession.selectList("allList");
	}
}
```

* **emp.xml**
src/main/resources/mapper 폴더 아래 있는 파일.   
root-context.xml 에서 SqlSessionFactory 클래스 설정시 작성한 mapperlocations의 위치와 동일한 곳에 있어야 한다.  
EmpDAOImpl 클래스의 메서드에서 호출한 `id`와 동일한 mapper가 실행되고 설정된 resultType으로 반환한다.  

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper
  PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
  "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
  
<!-- namespace 명은 패키지 포함해서 인터페이스 이름으로 작성해야 한다. 
	namespace는 mapper 들을 구분하는 식별자로 매우 중요하다. -->

<mapper namespace="com.spring.model.EmpDAO">

	<select id="allList" resultType="com.spring.model.EmpDTO">
		<!-- sql문 작성 -->
		select * from emp order by empno	
	</select>
	
</mapper>
```
