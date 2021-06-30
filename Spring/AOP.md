#SPRING

## 5. AOP(Aspect Oriented Programming : 관점 지향 프로그래밍)
기존의 OOP(Object Oriented Programming : 객체 지향 프로그래밍)를 보완한 개념.   


- 핵심사항과 공통관심사항을 분리하여 구현.   
- 문제를 바라보는 관점을 기준으로 프로그래밍을 하는 기법.
- AOP는 문제를 해결하기 위한 핵심 사항과 코드 전체에 적용되는 공통 관심 사항을 기준으로 프로그래밍 함으로써 공통 모듈을 여러 코드에 쉽게 적용할 수 있도록 돕는다.
- AOP는 핵심사항(primary(core) concern)과 공통관심사항(cross-cutting concern)을 별도의 코드로 구현하고 최종적으로 이를 조합해서 완성하는 것을 말한다.
- 기존의 코드를 보완한 개념(핵심사항과 공통관심사항을 분리하여 구현).

### 5.1. AOP의 장점
- 전체 코드에 흩어져 있는 공통관심사항이 하나의 장소에 집중(응집)된다.
- 서브스 모듈이 자신의 주요관심사항(핵심사항)에 대한 코드만 집중하고, 그외의 공통관심사항은 모두 빠지므로 코드가 깔끔해진다.
	
### 5.2. AOP의 주요 용어 - 중요!
- 핵심 관심 사항 : 비지니스 로직(주된 업무)
- 공통 관심 사항 : 부가적인 업무(보조 업무) - 횡단 관심 사항     
	공통 관심 사항은 누군가에게 맡겨 버리는 게 좋다.
- code : 핵심 관심 사항을 구현한 내용.
- Advice : 공통 관심 사항을 구현한 코드.      
	공통 관심 사항 내용을 정의하고 언제 그 작업을 수행할지를 정의하는 것.
	즉, 언제 공통 관심 기능을 핵심 로직에 적용할 지를 정의하고 있다.
- Aspect : 무엇을 언제 어디서 할지 등 필요한 정보가 정의되어 있다.      
		즉, 여러 객체에 공통으로 적용되고 있는 공통 관심 사항을 말한다. 트랜잭션이나 보안, 로그 등이 좋은 예.
- JoinPoint : Advice가 적용될 위치.(메서드 호출) Code와 Advice를 연결해 주는 설정 정보를 말한다.
- PointCut : JoinPoint의 부분집합으로써 실제 Advice가 적용되는 JoinPoint를 말한다.     
	스프링에서는 정규 표현식이나 AspectJ 문법을 이용하여 정의한다.
- Weaving : Code, Advice, PointCut 등을 조합해서 애플리케이션을 만들어가는 과정.    
	
* 스프링은 자체적인 프록시(대행) 기반의 AOP를 지원     
스프링은 공통 관심 사항(Aspect)의 적용 대상이 되는 객체에 프록시를 만들어서 제공하며, 대상 객체를 사용하는 코드는 대상 객체에 직접 접근하기 보다는 프록시를 통해서 간접적으로 접근한다.

### 5.3. 스프링에서 AOP 구현하는 방법
1. 설정 파일을 이용하는 방법(XML 기반의 구현 방법)
2. 애노테이션을 이용하는 방법(`@AspectJ` 애노테이션 기반의 AOP 구현)
- 스프링 AOP 사용시 라이브러리 등록(pom.xml)
	* artifactId가` aspectjweaver` 인 라이브러리를 등록해야 한다.
- 스프링 AOP 프록시 사용 시 라이브러리 등록(pom.xml)
	* artifactId가 `cglib` 인 라이브러리를 등록해야 한다.
	
3. 공통 기능 클래스 제작 - Advice 역할을 하는 클래스.
	
### 5.4. XML(설정 파일을 이용하는 방법) 파일에서 Advice 종류
* `<aop:before>` : 핵심 기능이 실행되기 전에 Advice(공통 관심 사항)를 실행.
* `<aop:after-returning>` : 정상적으로 핵심 기능이 실행된 이후에 Advice(공통 관심 사항)를 실행.
* `<aop:after-throwing>` : 핵심 기능 실행 중에 Exception이 발생 시 Advice(공통 관심 사항)을 실행.
* `<aop:after>` : Exception이 발생하더라도  핵심 기능 실행 후에 Advice(공통 관심 사항)을 실행. 
* `<aop:around>` : 핵심 기능 실행 전/후 및 Exception 발생 시 Advice(공통 관심 사항)을 실행. => 가장 많이 사용.
		
### 5.5. Aspect PointCut 표현식
- pointCut 을 지정할 때 사용하는 표현식으로 AspectJ 문법 사용.    
pointCut으로 표현할 수 있는 명시자에는 여러 종류가 있지만 일반적으로 가장 많이 사용하는 명시자는 execution 명시자이다. 그 외에도 within, bean 명시자가 있다.  
	- * : 모든
	- . : 현재
	- .. : 0개 이상
			
- execution 명시자 : Advice를 적용할 메서드를 명시할 때 사용.
	* `execution(public void get*(..))`
		=> public void 이고 메서드 이름이 get으로 시작하고 인자가 있는 경우.  
	* `execution(*.com.test.aop.*.*())`     
		=> com.test.aop 패키지의 모든 클래스에 파라미터(인자)가 없는 모든 메서드.
	* `execution(* com.test.aop..*.*())`    
		=> com.test.aop 패키지 및 com.test.aop 하위 패키지의 모든 클래스에 파라미터(인자)가 없는 모든 메서드.
	* `execution(* com.test.aop.Staff.*())`    
		=> com.test.aop 패키지 안의 Staff 클래스 안에 인자가 없는 모든 메서드.  
		
		
#### [예] 5.3. 스프링에서 AOP 구현하는 방법

자바에서 작성시 핵심 사항, 핵심 기능 이후, 예외 사항, 예외 발생하더라도 실행되는 사항들을 구분하여 작성하려면 아래와 같이 작성해야 한다.    
이를 좀 더 명료하게 작성하는 방법 3가지를 살펴볼 것이다.    

```java
/*
 * 여자(청소년) 
 * - 수업 끝나고 집에 와서 문을 열고 집에 들어갑니다.	=> 공통 관심 사항(before)
 * - TV로 드라마를 봅니다.					=> 핵심 사항
 * - 잠을 잡니다.							=> 공통 관심 사항(after-returning)
 * - 화재 발생 : 119에 신고					=> 공통 관심 사항(after-throwing)
 * - 아침에 일어나서 문을 열고 집을 나섭니다.		=> 공통 관심 사항(after)
 */

public class Girl implements Person {
	@Override
	public void doSomething() {	// 핵심 사항
		System.out.println("TV로 드라마를 봅니다.");
	}
}

/*
 * 남자(청소년) 
 * - 수업 끝나고 집에 와서 문을 열고 집에 들어갑니다.	=> 공통 관심 사항(before)
 * - 컴퓨터로 게임을 합니다.					=> 핵심 사항
 * - 잠을 잡니다.							=> 공통 관심 사항(after-returning)
 * - 화재 발생 : 119에 신고					=> 공통 관심 사항(after-throwing)
 * - 아침에 일어나서 문을 열고 집을 나섭니다.		=> 공통 관심 사항(after)
 */
public class Boy implements Person {
	@Override
	public void doSomething() {	// 핵심 사항
		System.out.println("컴퓨터로 게임을 합니다.");
	}
}
```

```java
public class PersonAdvice implements Person {
	@Override
	public void doSomething() {
	
		// 핵심 기능 이전(before)
		System.out.println("수업 끝나고 집에 와서 문을 열고 집에 들어갑니다.");
			
		try {
			person.doSomething(); 					// 핵심 사항
			System.out.println("잠을 잡니다.");			// 핵심 기능 이후(after-returning)
		}catch (Exception e) {
			System.out.println("화재 발생 : 119에 신고");	// 예외 사항(after-throwing)
		}finally {
			// 예외가 발생하더라도 실행되는 사항(after)
			System.out.println("아침에 일어나서 문을 열고 집을 나섭니다.");
		}
	}
}
```

```java
public class Main {
	public static void main(String[] args) {
		
		Person boy = new Boy();
		Person girl = new Girl();
		PersonAdvice advice = new PersonAdvice();
		
		advice.setPerson(boy);
		advice.doSomething();
		
		System.out.println("===================");
		
		advice.setPerson(girl);
		advice.doSomething();
	}
}
```
---

#### [예] 5.3. 스프링에서 AOP 구현하는 방법 - 1. 설정 파일을 이용하는 방법(XML 기반의 구현 방법)

* **MyAspect 클래스**
공통 관심 사항이 있는 코드들을 묶은 클래스를 만든다.   

```xml
// 스프링 AOP에서 공통 관심 사항이 있는 코드들의 묶음 ==> Advice
public class MyAspect {
	private double time;
	
	public void before() {
		time = System.nanoTime();
		System.out.println("수업 끝나고 집에 와서 문을 열고 집에 들어갑니다.");
	}
	
	public void af() {
		time = System.nanoTime() - time;
		System.out.println("아침에 일어나서 문을 열고 집을 나섭니다.");
	}
	
	public void after_returning() {
		System.out.println("잠을 잡니다.");	
	}
	
	public void after_throwing() {
		System.out.println("화재 발생 : 119에 신고");	
	}
}
```


* **aop02.xml**

Namespaces 에서 `aop` 체크.    
`aop:aspect` 태그 안에 `pointcut`(핵심 기능)을 중심으로 공통 관심 사항을 설정한다.  
MyAspect 클래스에서 설정한 메서드명을 각각의 공통 관심 사항의 method로 설정한다.   


```xml
<bean id="boy" class="com.sist.aop02.Boy" />
<bean id="girl" class="com.sist.aop02.Girl" />
<bean id="myaspect" class="com.sist.aop02.MyAspect" />
	
<aop:config>
	<!-- <aop:aspect> : 공통 관심 사항이 있는 클래스 설정 -->
	<aop:aspect ref="myaspect">
		<!-- 클래스 이름과 상관없이 doSomething()메서드가 pointCut(핵심 기능 갖는)이 된다는 의미 -->
		<aop:pointcut expression="execution(* doSomething())" id="myPointcut"/>
		<aop:before method="before" pointcut-ref="myPointcut"/>
		<aop:after method="af" pointcut-ref="myPointcut"/>
		<aop:after-returning method="after_returning" pointcut-ref="myPointcut"/>
		<aop:after-throwing method="after_throwing" pointcut-ref="myPointcut"/>
	</aop:aspect>
</aop:config>
```

그리고 메인에서 호출하여 출력한다.   

```java
AbstractApplicationContext ctx = new GenericXmlApplicationContext("classpath:aop02.xml");
		
Person boy = (Person)ctx.getBean("boy");
boy.doSomething();

Person girl = (Person)ctx.getBean("boy");
girl.doSomething();
		
ctx.close();
```

---

#### [예] 5.3. 스프링에서 AOP 구현하는 방법 - 2. 애노테이션을 이용하는 방법(`@AspectJ` 애노테이션 기반의 AOP 구현)


* **MyAspect 클래스** 
공통 관심 사항이 있는 코드들을 묶어서 클래스로 선언한다.    
이때 공통 관심 사항에 따라 애노테이션을 지정하고 괄호 안에 `execution( 핵심 사항 )`을 지정하여  `pointcut`으로 잡아준다.   
이 `pointcut`이 기준이 된다.  

```java
// 스프링 AOP에서 공통 관심 사항이 있는 코드들의 묶음 ==> Advice
@Component
@Aspect
public class MyAspect {
	private double time;
	
	@Pointcut("execution(* doSomething())")	// 어느 클래스든 doSomething() 이 pointcut이 된다
	public void myPointcut() { }
	
	@Before("myPointcut()")	// myPointcut() 메서드 이전에 실행
	public void before() {
		time = System.nanoTime();
		System.out.println("수업 끝나고 집에 와서 문을 열고 집에 들어갑니다.");
	}
	
	@After("myPointcut()")
	public void af() {
		time = System.nanoTime() - time;
		System.out.println("아침에 일어나서 문을 열고 집을 나섭니다.");
		System.out.println("걸린 시간 : " + time + "ns");
	}
	
	@AfterReturning("myPointcut()")
	public void after_returning() {
		System.out.println("잠을 잡니다.");	
	}
	
	@AfterThrowing("myPointcut()")
	public void after_throwing() {
		System.out.println("화재 발생 : 119에 신고");	
	}
}
```


* **aop3.xml**
Namespaces 에서 `aop` 체크.  
`@AspectJ`가 붙어있는 빈이 자동으로 Aspect가 될 수 있도록 태그를 생성한다.  

```xml
<context:component-scan base-package="com.sist.aop03" />
	
<!-- @AspectJ가 붙어 있는 빈을 자동으로 Aspect가 될 수 있게 해 주는 태그 -->
<aop:aspectj-autoproxy />
```

앞의 방법과 동일하게 main에서 호출하고 출력한다.    
xml 파일에 태그 한 줄을 작성하고, 공통 관심 사항 메서드에 각각의 애노테이션을 지정함으로써 간단하게 aop 구현이 가능하다.   


---
#### [예] 5.3. 스프링에서 AOP 구현하는 방법 - 3. 공통 기능 클래스 제작 - Advice 역할을 하는 클래스.

* **AdviceLog 클래스**

```java
public class AdviceLog {
	
	// ProceedingJoinPoint 객체는 원래 실행되어야 할 대상 메서드(핵심 기능) 대행(프록시) 객체
	public Object profile(ProceedingJoinPoint jp) throws Throwable {
		
		// getSignature() : 호출되는 메서드에 대한 정보를 알려주는 메서드.
		String signStr = jp.getSignature().toString();
		System.out.println(signStr + "is start.");
		
		long startTime = System.nanoTime();
		
		Object obj = jp.proceed();	// 핵심 기능을 실행시키는 메서드.
		
		long endTime = System.nanoTime();
		System.out.println(signStr + "is end.");
		System.out.println("경과 시간 : " + (endTime-startTime));
		
		return obj;
	}
}
```

* **aop04.xml**

`before`, `after` 등 공통 관심 사항을 하나의 태그 `<aop:pointcut>`으로 묶어서 설정한다.  

```xml
<!-- xml 파일로 DI할 설정들 작성 후 아래 코드 작성 -->

<bean id="advice" class="com.sist.aop04.AdviceLog" />

<aop:config>
	<aop:aspect ref="advice">
		<aop:pointcut expression="within(com.sist.aop04.*)" id="mypointcut"/>
		<!-- aop:around : before, after 등 전부 적용 -->
		<aop:around method="profile" pointcut-ref="mypointcut" />
	</aop:aspect>
</aop:config>
```

앞의 방법과 동일하게 main에서 호출하고 출력한다.    
반복적으로 작성하지 않아도 `<aop:pointcut>` 하나로 깔끔하게 정리가 가능하다.   
















		