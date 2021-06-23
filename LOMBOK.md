# LOMBOK

애노테이션(annotation) 중의 하나.

## 1. 설정 방법
1. <a href="projectlombok.org/download">projectlombok.org/download</a> - Download 1.18.20
2. 다운로드 받은 파일 실행 - Specify Location - 스프링 설치 경로(sts.exe) 설정 - install/update - Quit Installer
3. pom.xml 에 lombok 라이브러리 추가
	1. <a href="mvnrepository.com">mvnrepository.com</a> - lombok search 
	2. Project Lombok - 1.18.20 - Maven 코드 복사
	3. pom.xml 파일에서 <dependency> 태그들 사이에 붙여넣기

```xml
<!-- lombok 라이브러리 -->
<dependency>
	<groupId>org.projectlombok</groupId>
	<artifactId>lombok</artifactId>
	<version>1.18.20</version>
	<scope>provided</scope>
</dependency>
```
4. 필요한 클래스 상단에 애노테이션(`@`) 추가


## 2. 종류

```java
@Data				// getter/setter
@NoArgsConstructor	// 인자를 가지지 않는 생성자
@AllArgsConstructor	// 모든 멤버를 인자로 가지는 인자생성자
```

