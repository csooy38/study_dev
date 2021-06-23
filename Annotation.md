# Annotation

> 스프링 애노테이션(annotation).

## 1. 설정 방법
1. pom.xml 에 라이브러리 추가
	1. <a href="http://mvnrepository.com">mvnrepository.com</a> - 애노테이션 이름 search 
	2. 버전에 맞는 라이브러리 선택 - Maven 코드 복사
	3. pom.xml 파일에서 <dependency> 태그들 사이에 붙여넣기
	4. 필요한 클래스 상단에 애노테이션(`@`) 추가

	
---
### * Lombok 
1. 추가방법
	* 방법 1
		1. <a href="http://projectlombok.org/download">projectlombok.org/download</a> - Download 1.18.20
		2. 다운로드 받은 파일 실행 - Specify Location - 스프링 설치 경로(sts.exe) 설정 - install/update - Quit Installer

	* 방법 2
		* pom.xml 에 라이브러리 추가

		```xml
		<!-- lombok 라이브러리 -->
		<dependency>
			<groupId>org.projectlombok</groupId>
			<artifactId>lombok</artifactId>
			<version>1.18.20</version>
			<scope>provided</scope>
		</dependency>
		```

2. 종류

	```java
	@Data			// getter/setter
	@NoArgsConstructor	// 인자를 가지지 않는 생성자
	@AllArgsConstructor	// 모든 멤버를 인자로 가지는 인자생성자
	```

---

### * cglib

1. 애노테이션 역할
	* 컴파일러에게 정보를 알려주는 역할.
	* 컴파일 할 때와 설치 시의 작업을 지정하는 역할.
	* 실행할 때에 별도의 처리가 필요한 경우 사용되는 역할.


2. 추가방법 : pom.xml에 cglib 라이브러리 추가.

	```xml
	<!-- https://mvnrepository.com/artifact/cglib/cglib -->
	<dependency>
	    <groupId>cglib</groupId>
	    <artifactId>cglib</artifactId>
	    <version>2.2.2</version>
	</dependency>
	```

3. 종류

	```java
	@Configuration	// 클래스 앞에 선언하는 애노테이션. "해당 클래스는 스프링 설정에 사용되는 클래스입니다."라고 알려주는 애노테이션.
	@bean 		// 메소드 앞에 사용되는 애노테이션. "해당 메서드는 객체를 생성하는데 사용됩니다." 의미.
	```


